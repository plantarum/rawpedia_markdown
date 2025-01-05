This guide documents how to build RawTherapee for 32-bit or 64-bit
versions of Windows using the MinGW-w64 runtime. Begin by installing and
updating MSYS2 using the instructions from
[1](https://msys2.github.io/). Then run the following commands using
either *MinGW-w64 Win32 Shell* or *MinGW-w64 Win64 Shell* depending on
whether you want to build a 32-bit or a 64-bit version.

## Install tools and libraries

First, install a few miscellaneous tools

    $ pacman -S tar gzip nano make diffutils intltool git

Then install the necessary development tools

    # win32
    $ pacman -S mingw-w64-i686-gcc mingw-w64-i686-gdb mingw-w64-i686-make mingw-w64-i686-pkg-config mingw-w64-i686-cmake
    # win64
    $ pacman -S mingw-w64-x86_64-gcc mingw-w64-x86_64-gdb mingw-w64-x86_64-make mingw-w64-x86_64-pkg-config mingw-w64-x86_64-cmake

and the required libraries

    # win32
    $ pacman -S mingw-w64-i686-gtkmm mingw-w64-i686-gtkmm3 mingw-w64-i686-lcms2 mingw-w64-i686-fftw
    # win64
    $ pacman -S mingw-w64-x86_64-gtkmm mingw-w64-x86_64-gtkmm3 mingw-w64-x86_64-lcms2 mingw-w64-x86_64-fftw

## Download and build libiptcdata

The libiptcdata library is not yet provided by MSYS2, therefore it
should be downloaded and configured using

    $ curl -LO http://downloads.sourceforge.net/project/libiptcdata/libiptcdata/1.0.4/libiptcdata-1.0.4.tar.gz
    $ tar xzf libiptcdata-1.0.4.tar.gz
    $ cd libiptcdata-1.0.4

    # win32
    $ ./configure --prefix=/mingw32
    # win64
    $ ./configure --prefix=/mingw64

Afterwards *Makefile* needs to be opened using a text editor to remove
*iptc* and *docs* from the lists named *SUBDIRS* and *DIST_SUBDIRS* as
building or installing will fail otherwise.

    $ nano Makefile

    # Replace
    DIST_SUBDIRS = m4 libiptcdata po iptc docs win python
    # by
    DIST_SUBDIRS = m4 libiptcdata po win python

    # And replace
    SUBDIRS = m4 libiptcdata po iptc docs win $(MAYBE_PYTHONLIB)
    # by
    SUBDIRS = m4 libiptcdata po win $(MAYBE_PYTHONLIB)

Finally build and install the library

    $ make
    $ make install
    $ cd

## Download and build Clearlooks

RawTherapee versions that use version 2 of Gtk+ need the Clearlooks
theme engine which can be downloaded and built using

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

First, clone RawTherapee's Git repository

    $ git clone http://github.com/Beep6581/RawTherapee.git
    $ cd RawTherapee

and optionally checkout a specific branch if you do not want to build
the default *master*, e.g.

    $ git checkout gtk3

Then, create a separate directory for the build

    $ mkdir build
    $ cd build

and run CMake and Make

    $ cmake -G "MSYS Makefiles" -DCMAKE_BUILD_TYPE="debug" -DPROC_TARGET_NUMBER="2" -DBUILD_BUNDLE="ON" -DCMAKE_INSTALL_PREFIX="." -DBINDIR="." -DDATADIR="." -DCACHE_NAME_SUFFIX=4 ..
    $ make -j8
    $ make install

Please refer to the [Linux](Linux "wikilink") article for an explanation
of the various options passed to CMake and Make.

If you are doing an optimized build, e.g. *release* or *relwithdebinfo*,
for older 32-bit versions of Windows like XP, you will need to add the
*-mstackrealign* compiler flag, i.e.

    -DCMAKE_C_FLAGS="-mstackrealign" -DCMAKE_CXX_FLAGS="-mstackrealign"

## Copy RawTherapee and required DLL

RawTherapee can now be started from the MSYS2 command line

    # for debug builds
    $ cd debug
    # for release builds
    $ cd release
    $ ./rawtherapee.exe

The file manager can be used to copy the contents of
*<MSYS2>\home\\<User>\RawTherapee\build\\debug\|release\>* together with
the necessary DLL from *<MSYS2>\\mingw32\|mingw64\>\bin* into a
RawTherapee installation folder, where *<MSYS2>* is the MSYS2
installation folder and *<User>* the Windows user name.

A (possibly incomplete) list of required DLL is

    libatk-1.0-0.dll
    libatkmm-1.6-1.dll
    libbz2-1.dll
    libcairo-2.dll
    libcairo-gobject-2.dll
    libcairomm-1.0-1.dll
    libepoxy-0.dll
    libexpat-1.dll
    libffi-6.dll
    libfftw3f-3.dll
    libfontconfig-1.dll
    libfreetype-6.dll
    libgcc_s_dw2-1.dll|libgcc_s_seh-1.dll
    libgdk-3-0.dll
    libgdk-win32-2.0-0.dll
    libgdkmm-2.4-1.dll
    libgdkmm-3.0-1.dll
    libgdk_pixbuf-2.0-0.dll
    libgio-2.0-0.dll
    libgiomm-2.4-1.dll
    libglib-2.0-0.dll
    libglibmm-2.4-1.dll
    libgmodule-2.0-0.dll
    libgobject-2.0-0.dll
    libgomp-1.dll
    libgtk-3-0.dll
    libgtk-win32-2.0-0.dll
    libgtkmm-2.4-1.dll
    libgtkmm-3.0-1.dll
    libharfbuzz-0.dll
    libiconv-2.dll
    libintl-8.dll
    libjpeg-8.dll
    liblcms2-2.dll
    liblzma-5.dll
    libpango-1.0-0.dll
    libpangocairo-1.0-0.dll
    libpangoft2-1.0-0.dll
    libpangomm-1.4-1.dll
    libpangowin32-1.0-0.dll
    libpixman-1-0.dll
    libpng16-16.dll
    libsigc-2.0-0.dll
    libstdc++-6.dll
    libtiff-5.dll
    libwinpthread-1.dll
    zlib1.dll

The following files also need to be copied

    <prefix>\bin\gspawn-<win32|win64>-helper.exe -> .
    <prefix>\bin\gspawn-<win32|win64>-helper-console.exe -> .

    <prefix>\lib\gtk-2.0\include -> .
    <prefix>\lib\gtk-2.0\modules -> .
    <prefix>\lib\gtk-2.0\2.10.0\engines -> .

    <prefix>\share\glib-2.0\schemas\gschemas.compiled -> .\share\glib-2.0\schemas

where *<prefix>* is *<MSYS2>\\mingw32\|mingw64\>* from above and *.* is
the installation folder.

## Creating a distributable package

If you plan to distribute Rawtherapee packages for the Windows platform,
as a first step you need to make sure that Rawtherapee will be built for
the generic processor target. To do so, use `-DPROC_TARGET_NUMBER="1"`
in the cmake command.

During compilation, a script named *WindowsInnoSetup.iss* is created in
the Rawtherapee installation folder. This script is used by Inno Setup
[2](http://www.jrsoftware.org/isinfo.php), a program which is used to
generate installers for Windows programs. It is advised to download the
Unicode version
[3](http://www.jrsoftware.org/download.php/is-unicode.exe) to avoid
problems with some languages. The current *WindowsInnoSetup.iss* script
is designed for the current master branch (Gtk+2). If you want to create
a package from the Gtk3 branch, you will need to edit the script and
replace the line

    Source: "{#MyBuildBasePath}\lib\*"; DestDir: "{app}\lib\"; Flags: ignoreversion recursesubdirs createallsubdirs

with

    Source: "{#MyBuildBasePath}\share\*"; DestDir: "{app}\share\"; Flags: ignoreversion recursesubdirs createallsubdirs

so that icons and schemas will be copied into the package.

To help users [filing useful bug
reports](http://50.87.144.65/~rt/w/index.php?title=How_to_write_useful_bug_reports),
package maintainers are encouraged to produce Debug builds along each of
their Release builds, and to bundle them with the gdb debugger
executable. Windows binaries of the debugger (gdb.exe) can be downloaded
from [here](http://www.equation.com/servlet/equation.cmd?fa=gdb) in 32
and 64 bits versions.

The *gdb.exe* binary should be copied in Rawtherapee installation folder
and, if using Inno Setup to generate the package, the
*WindowsInnoSetup.iss* script should be edited by adding the following
line around line 121 of the script:

    Source: "{#MyBuildBasePath}\gdb.exe"; DestDir: "{app}"; Flags: ignoreversion

Note that GDB is a program released under GNU GPL license, its soure
code can be downloaded at <http://www.gnu.org/software/gdb/>.

Now that everything is set up, to create the package right click on the
*WindowsInnoSetup.iss* script and choose *Compile* from the context
menu. It will automatically generate the installer and place it in the
parent folder. To make your new package compatible with the official
Rawtherapee website uploader, create a zip archive in which you'll place
both the newly created installer and the corresponding
*AboutThisBuild.txt* which should be found at the same place. Name the
resulting zip archive following this template:
RawTherapee_\<WinXP\|WinVista\>_\<32\|64\>_branch_buildtype_version.zip
(for example, Rawtherapee_WinVista_64_gtk3_Release_4.2.730.zip).