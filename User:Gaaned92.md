This guide documents how to build RawTherapee for 32-bit or 64-bit
versions of Windows using the MinGW-w64 runtime.

## MSYS2 Installation

Begin by installing and updating MSYS2 carefully following the
instructions from the [MSYS2 website](https://msys2.github.io/). Then
run the following commands using either "*MinGW-w64 Win32 Shell*" if you
want to build a 32-bit version, or "*MinGW-w64 Win64 Shell*" if you want
to build a 64-bit version.

RawTherapee can be built using GTK+ versions 2 or 3. To build using GTK2
use the `gtk2` branch; to build using GTK3 use the `dev` branch. The
last version of RawTherapee to support GTK2 is 5.0-r1-gtk2 released on
2017-02-02. Use the `dev` branch for the latest code - it requires GTK+
\>=3.16. We recommend using GTK+ 3.22.24 or newer as this is the first
version to support native windows, without which the RawTherapee window
could exhibit [strange
behavior](https://github.com/Beep6581/RawTherapee/issues/4125) such as
maximizing under the taskbar in Windows 10.

## Install tools and libraries

First, install a few miscellaneous tools:

    $ pacman -S tar gzip nano make diffutils intltool git

Then install the necessary development tools:

    # win32
    $ pacman -S mingw-w64-i686-gcc mingw-w64-i686-gdb mingw-w64-i686-make mingw-w64-i686-pkg-config mingw-w64-i686-cmake
    # win64
    $ pacman -S mingw-w64-x86_64-gcc mingw-w64-x86_64-gdb mingw-w64-x86_64-make mingw-w64-x86_64-pkg-config mingw-w64-x86_64-cmake

and the required libraries:

    # win32
    $ pacman -S mingw-w64-i686-gtkmm mingw-w64-i686-gtkmm3 mingw-w64-i686-lcms2 mingw-w64-i686-fftw
    # win64
    $ pacman -S mingw-w64-x86_64-gtkmm mingw-w64-x86_64-gtkmm3 mingw-w64-x86_64-lcms2 mingw-w64-x86_64-fftw mingw-w64-x86_64-lensfun

## Download and build libiptcdata

The libiptcdata library is not yet provided by MSYS2, therefore it
should be downloaded and configured using:

    $ curl -LO http://downloads.sourceforge.net/project/libiptcdata/libiptcdata/1.0.4/libiptcdata-1.0.4.tar.gz
    $ tar xzf libiptcdata-1.0.4.tar.gz
    $ cd libiptcdata-1.0.4

    # win32
    $ ./configure --prefix=/mingw32
    # win64
    $ ./configure --prefix=/mingw64

Afterwards the `Makefile` needs to be opened using a text editor to
remove `iptc` and `docs` from the lists named `SUBDIRS` and
`DIST_SUBDIRS`, as building or installing will fail otherwise:

    $ nano Makefile

    # Replace
    DIST_SUBDIRS = m4 libiptcdata po iptc docs win python
    # with
    DIST_SUBDIRS = m4 libiptcdata po win python

    # And replace
    SUBDIRS = m4 libiptcdata po iptc docs win $(MAYBE_PYTHONLIB)
    # with
    SUBDIRS = m4 libiptcdata po win $(MAYBE_PYTHONLIB)

Finally build and install the library:

    $ make
    $ make install
    $ cd

## Download and build Clearlooks

If you are building RawTherapee using GTK2 then you need the Clearlooks
theme engine. You do not need it if you are building using GTK3.

Download and build it:

    $ curl -LO http://sources.archlinux.org/other/gtk-engines/gtk-engines-2.21.0.tar.gz
    $ tar xzf gtk-engines-2.21.0.tar.gz
    $ cd gtk-engines-2.21.0

    # win32
    $ ./configure --prefix=/mingw32 --disable-all --enable-clearlooks
    # win64
    $ ./configure --prefix=/mingw64 --disable-all --enable-clearlooks

    $ make
    $ make install
    $ cd

## Clone and build RawTherapee

Clone RawTherapee's Git repository. The build process will fail if there
is a space character anywhere in your `build` folder path. For example
if your Windows username is "Zank Frappa" then your home path will be
`C:\Users\Zank Frappa\` and if you clone RawTherapee inside there then
the build will fail during compilation. Simply clone to a folder where
neither it nor its parent folders have a space in their name, for
example `C:\code\repo-rt`

    $ git clone http://github.com/Beep6581/RawTherapee.git /c/code/repo-rt
    $ cd /c/code/repo-rt

RawTherapee can be built using GTK+ versions 2 or 3. To build using GTK2
use the `gtk2` branch; to build using GTK3 use the `dev` branch. The
last version of RawTherapee to support GTK2 is 5.0-r1-gtk2 released on
2017-02-02. Use the `dev` branch for the latest code - it requires GTK+
\>=3.16. When you clone the repository you will automatically find
yourself in the `dev` branch. To switch to the `dev` branch manually, do
the following:

    $ git checkout dev

Create a separate directory for the build:

    $ mkdir build
    $ cd build

Note that if you switch branches then you must delete and recreate the
`build` folder so that compilation starts from scratch in an empty
folder, otherwise compilation is likely to fail. However if you are just
updating without changing branches then you do not have to start with an
empty build folder - you can just go into the existing one, and
compilation will be faster because not everything will need to be
recompiled.

Run CMake and Make:

    $ cmake -G "MSYS Makefiles" -DLENSFUNDBDIR=share/lensfun -DCMAKE_BUILD_TYPE="release" -DPROC_TARGET_NUMBER="2" -DCACHE_NAME_SUFFIX="5-dev" ..
    $ make install

You can find an explanation of the various CMake options in the [Linux
article](Linux#CMake "wikilink"), including an explanation of the
various "BUILD_TYPE" options.

If you are building for 32-bit Windows XP and are using the `release` or
`relwithdebinfo` "BUILD_TYPE", you will need to add the `-mstackrealign`
compiler flag before the last two dots `..` of the CMake command above:

    -DCMAKE_C_FLAGS="-mstackrealign" -DCMAKE_CXX_FLAGS="-mstackrealign"

## Copy RawTherapee and required DLLs

RawTherapee can now be started from the MSYS2 command line:

    # for debug builds
    $ cd debug
    # for release builds
    $ cd release
    # for relwithdebinfo builds
    $ cd relwithdebinfo
    $ ./rawtherapee.exe

The file manager can be used to copy the contents of
`c:\code\repo-rt\build\<debug|release|relwithdebinfo>` together with the
necessary DLLs from <prefix>`\bin` into `.`, where:

- <prefix> is <MSYS2>`\<mingw32|mingw64>`,
- <MSYS2> is the MSYS2 installation folder,
- and `.` is the RawTherapee installation folder.

The current list of required DLLs is:

    libatk-1.0-0.dll
    libatkmm-1.6-1.dll
    libbz2-1.dll
    libcairo-2.dll
    libcairo-gobject-2.dll
    libcairomm-1.0-1.dll
    libcroco-0.6-3.dll
    libepoxy-0.dll
    libexpat-1.dll
    libfﬁ-6.dll
    libfftw3f-3.dll
    libfontconﬁg-1.dll
    libfreetype-6.dll
    libgcc_s_seh-1.dll
    libgdk_pixbuf-2.0-0.dll
    libgdk-3-0.dll
    libgdkmm-3.0-1.dll
    libgio-2.0-0.dll
    libgiomm-2.4-1.dll
    libglib-2.0-0.dll
    libglibmm-2.4-1.dll
    libgmodule-2.0-0.dll
    libgobject-2.0-0.dll
    libgomp-1.dll
    libgraphite2.dll
    libgtk-3-0.dll
    libgtkmm-3.0-1.dll
    libharfbuzz-0.dll
    libiconv-2.dll
    libintl-8.dll
    libjpeg-8.dll
    liblcms2-2.dll
    liblensfun.dll
    liblzma-5.dll
    libpango-1.0-0.dll
    libpangocairo-1.0-0.dll
    libpangoft2-1.0-0.dll
    libpangomm-1.4-1.dll
    libpangowin32-1.0-0.dll
    libpcre-1.dll
    libpixman-1-0.dll
    libpng16-16.dll
    librsvg-2-2.dll
    libsigc-2.0-0.dll
    libstdc++-6.dll
    libsystre-0.dll
    libtiff-5.dll
    libtre-5.dll
    libwinpthread-1.dll
    libxml2-2.dll
    zlib1.dll

The following list of Adwaita theme files should be copied from
<prefix>`\share\icons\Adwaita\` to `.\share\icons\Adwaita\`:

    16x16\actions\*
    16x16\devices\*
    16x16\mimetypes\*
    16x16\places\*
    16x16\status\*
    48x48\devices\*
    24x24\status\image-missing.png

    icon-theme.cache
    index.theme

    cursors\plus.cur
    cursors\sb_h_double_arrow.cur
    cursors\sb_left_arrow.cur
    cursors\sb_right_arrow.cur
    cursors\sb_v_double_arrow.cur

The following files also need to be copied:

    <prefix>\bin\gspawn-<win32|win64>-helper.exe -> .
    <prefix>\bin\gspawn-<win32|win64>-helper-console.exe -> .

    <prefix>\lib\gdk-pixbuf-2.0 -> .\lib\gdk-pixbuf-2.0

    <prefix>\share\glib-2.0\schemas\gschemas.compiled -> .\share\glib-2.0\schemas
    <prefix>\share\lensfun\version_1\* -> .\share\lensfun

## Creating a distributable package

If you plan to distribute RawTherapee packages for the Windows platform,
as a first step you need to make sure that RawTherapee will be built for
the "generic" processor target. To do so, use `-DPROC_TARGET_NUMBER="1"`
in the CMake command.

During compilation, a script named `WindowsInnoSetup.iss` is created in
the RawTherapee installation folder. This script is used by Inno Setup
[1](http://www.jrsoftware.org/isinfo.php), a program which is used to
generate installers for Windows programs. It is advised to download the
Unicode version
[2](http://www.jrsoftware.org/download.php/is-unicode.exe) to avoid
problems with some languages.

The current `WindowsInnoSetup.iss` script is designed for the `gtk2`
branch. If you want to create a package for a GTK3 build (`dev` or
`releases` branches) you will need to edit the script and replace the
line:

    Source: "{#MyBuildBasePath}\lib\*"; DestDir: "{app}\lib\"; Flags: ignoreversion recursesubdirs createallsubdirs

with

    Source: "{#MyBuildBasePath}\share\*"; DestDir: "{app}\share\"; Flags: ignoreversion recursesubdirs createallsubdirs

so that icons and schemas will be copied into the package.

To help users [write useful bug
reports](How_to_write_useful_bug_reports "wikilink"), package
maintainers are encouraged to produce builds which include both a
"release" and a "debug" executable, and to bundle them together with the
GDB debugger executable. In other words, put the `rawtherapee.exe`
(release) file together with the `rawtherapee-debug.exe` (debug) file
and the `gdb.exe` file together into the same installer or the same
archive. An alternative is to produce "relwithdebinfo" builds - these
are much faster than "debug" but not as optimized as "release" builds,
yet they provide just about as much useful information as "debug"
builds. When making "relwithdebinfo" or "debug" builds you must provide
the GDB debugger executable. Windows binaries of the debugger `gdb.exe`
can be downloaded from
[here](http://www.equation.com/servlet/equation.cmd?fa=gdb) in 32- and
64-bit versions.

The `gdb.exe` binary, available from <http://www.gnu.org/software/gdb/>,
should be copied into the RawTherapee installation folder and, if using
Inno Setup to generate the package, the `WindowsInnoSetup.iss` script
should be edited by uncommenting (removing the semicolon from the front
of) the following around line 114 of the script:

    ;Source: "{#MyBuildBasePath}\gdb.exe"; DestDir: "{app}"; Flags: ignoreversion

Now that everything is set up, to create the package right-click on the
`WindowsInnoSetup.iss` script and choose *Compile* from the context
menu. It will automatically generate the installer and place it in the
parent folder.

To make your new package compatible with the RawTherapee website's
upload panel, create a zip archive in which you will place both the
newly created installer and the corresponding *AboutThisBuild.txt* file
which can be found at the same place. Name the resulting zip archive
following this template:
`RawTherapee_<WinXP|WinVista>_<32|64>_`<version>`_`<buildtype>`.zip`

- "WinXP" means that the build is only for Windows XP. "WinVista" means
  it can run on any version of Windows from Vista upwards, including 10.
- The "version" will either look like `5.2` if you checkout the `5.2`
  tag, or `5.2-dev-g1a2b3c4d` if you checkout the `dev` branch after 5.2
  was tagged.
- If you are shipping more than one build type in an installer, include
  the names of all build types, e.g. `release_debug`.

For example:

- `RawTherapee_WinVista_64_5.2_release.zip`
- `RawTherapee_WinVista_64_5.2_release_debug.zip`
- `RawTherapee_WinVista_64_5.2-dev-g1a2b3c4d_release_debug.zip`