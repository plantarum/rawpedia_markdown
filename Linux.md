This page details instructions for compiling RawTherapee on
**GNU/Linux** systems. There are also instructions for compiling on
[Windows](Windows "wikilink") and [OS X](OS_X "wikilink").

When in doubt, [join us on IRC](IRC "wikilink") and ask a human!

## Dependencies

To compile RawTherapee your system will need a set of tools. They are
called dependencies, and here is a list of them for the two main
branches, "master" which uses GTK+ 2 (GTK2) and "gtk3" which uses GTK+ 3
(GTK3):

| Branch       | Package      | Version             | Gentoo                 | Debian/Ubuntu        | URL                                                                                |
|--------------|--------------|---------------------|------------------------|----------------------|------------------------------------------------------------------------------------|
| master, gtk3 | BZIP2        | bzip2\>-1.0.4       | app-arch/bzip2         | libbz2-dev           | <http://www.bzip.org/>                                                             |
| master, gtk3 | EXIV2        | exiv2\>=0.19        | media-gfx/exiv2        | libexiv2-dev         | <http://www.exiv2.org/>                                                            |
| master, gtk3 | EXPAT        | expat\>=2.1.0       | dev-libs/expat         | libexpat-dev         | <http://expat.sourceforge.net/>                                                    |
| master, gtk3 | FFTW3        | fftw\>=3.2.2        | sci-libs/fftw          | fftw-dev             | <http://fftw.org/>                                                                 |
| master, gtk3 | GCC          | gcc\>=4.9           | sys-devel/gcc          | build-essential      | <http://gcc.gnu.org/>                                                              |
| master, gtk3 | GLIB2        | glib-2.0\>=2.24     | dev-libs/glib          | libglib2.0-dev       | <http://www.gtk.org/>                                                              |
| master, gtk3 | GLIBMM       | glibmm-2.4\>=2.24   | dev-cpp/glibmm         | libglibmm-2.4-dev    | <http://www.gtkmm.org>                                                             |
| master       | GTK+         | gtk+-2.0\>=2.24.18  | x11-libs/gtk+          | libgtk2.0-dev        | <http://www.gtk.org/>                                                              |
| gtk3         | GTK+         | gtk+-3.16           | x11-libs/gtk+          | libgtk-3-dev         | <http://www.gtk.org/>                                                              |
| master       | GTK2-Engines | gtk-engines-2.20.2  | x11-themes/gtk-engines | gtk2-engines         | <http://www.gtk.org/>                                                              |
| master       | GTKMM        | gtkmm-2.4\>=2.22    | dev-cpp/gtkmm          | libgtkmm-2.4-dev     | <http://www.gtkmm.org>                                                             |
| gtk3         | GTKMM        | gtkmm-3.16          | dev-cpp/gtkmm          | libgtkmm-3.0-dev     | <http://www.gtkmm.org>                                                             |
| master, gtk3 | JPEG         | libjpeg\>=6b        | media-libs/jpeg        | libjpeg-dev          | <http://libjpeg-turbo.virtualgl.org/> <http://jpegclub.org/> <http://www.ijg.org/> |
| master, gtk3 | LCMS2        | lcms\>=2.6          | media-libs/lcms        | liblcms2-dev         | <http://www.littlecms.com/>                                                        |
| master, gtk3 | LIBCANBERRA  | libcanberra\>=0.29  | media-libs/libcanberra | libcanberra-gtk3-dev | <http://0pointer.de/lennart/projects/libcanberra/> (Linux only)                    |
| master, gtk3 | LIBIPTCDATA  | libiptcdata\>=1.0.2 | media-libs/libiptcdata | libiptcdata-dev      | <http://libiptcdata.sourceforge.net>                                               |
| master, gtk3 | PNG          | libpng\>=1.2.44     | media-libs/libpng      | libpng-dev           | <http://www.libpng.org/>                                                           |
| master, gtk3 | SIGC         | sigc++-2.0          | dev-libs/libsigc++     | libsigc++-2.0-dev    | <http://libsigc.sourceforge.net/>                                                  |
| master, gtk3 | TIFF         | libtiff\>=3.9.4     | media-libs/tiff        | libtiff-dev          | <http://www.remotesensing.org/libtiff/>                                            |
| master, gtk3 | ZLIB         | zlib\>=1.2.3        | sys-libs/zlib          | zlib1g-dev           | <http://www.zlib.net/>                                                             |

Build-time dependencies for RawTherapee 4

To compile the outdated RawTherapee 3 you will need these:

| Package | Version     | Gentoo          | Debian/Ubuntu | URL                         |
|---------|-------------|-----------------|---------------|-----------------------------|
| LCMS1   | lcms\<=1.99 | media-libs/lcms | liblcms1-dev  | <http://www.littlecms.com/> |

Build-time dependencies for RawTherapee 3

In order to install all these dependencies, you will need to open a
console and paste the code from the appropriate section into the
console. Note that these code snippets include the GTK3 dependencies if
available, so if you want to compile the "master" branch which uses GTK2
then replace the GTK3 dependencies with GTK2 ones as described in the
list above.

### Arch

The latest Arch supports GTK3, use the `gtk3` branch. The dependencies
below are only for the `gtk3` branch.

    sudo pacman -S bzip2 exiv2 expat fftw glib2 glibmm gtk3 gtkmm3 lcms2 libcanberra libiptcdata libjpeg-turbo libpng libsigc++ libtiff zlib

### CentOS 7.1

CentOS 7.1 does not support a recent enough version of GTK3. As CentOS
7.1 does not seem to have the Clearlooks GTK2 theme engine, you will
either need to install some other GTK2 theme engine, or after installing
RawTherapee go to "Preferences \> General \> Default Theme" and enable
"Use system theme".

    sudo yum install bzip2-devel cmake curl exiv2-devel expat-devel fftw-devel gcc-c++ git glibmm24-devel gtk2-devel gtkmm24-devel lcms2-devel libjpeg-turbo-devel libcanberra-devel libiptcdata-devel libpng-devel libtiff-devel sigc++20-devel zlib-devel

### Fedora

Fedora 22 and 23 support GTK3, older versions do not, use the `gtk3`
branch on those versions of Fedora. The dependencies below are only for
the `gtk3` branch.

    sudo dnf install bzip2-devel cmake exiv2-devel expat-devel fftw-devel gcc-c++ glib2-devel glibmm24-devel gtk3-devel gtkmm30-devel lcms2-devel libcanberra-devel libiptcdata-devel libjpeg-turbo-devel libpng-devel libsigc++20-devel libtiff-devel zlib-devel

### Gentoo

Gentoo supports GTK3, use the `gtk3` branch. The dependencies below are
only for the `gtk3` branch.

    sudo emerge -uva app-arch/bzip2 dev-cpp/gtkmm:3.0 dev-libs/expat media-gfx/exiv2 media-libs/lcms media-libs/libcanberra media-libs/libiptcdata media-libs/libjpeg-turbo media-libs/libpng media-libs/tiff net-misc/curl sci-libs/fftw sys-libs/zlib x11-libs/gtk+:3

### openSUSE

openSUSE Tumbleweed supports GTK3, older versions do not. Use the `gtk3`
branch on Tumbleweed. The dependencies below are only for the `gtk3`
branch. Note: openSUSE 42.1 supports GTK+ 3.16.7 but compilation fails
as the sigc++-2.0\>=2.4 requirement is not met.

    sudo zypper in cmake fftw3-devel gcc-c++ glib2-devel glibmm2-devel gtk3-devel gtkmm3-devel libbz2-devel libcanberra-devel libexpat-devel libiptcdata-devel libjpeg-devel liblcms2-devel libpng-devel libsigc++2-devel libtiff-devel zlib-devel

### Sabayon

Sabayon supports GTK3, use the `gtk3` branch. The dependencies below are
only for the `gtk3` branch.

    sudo equo install app-arch/bzip2 dev-cpp/gtkmm:3.0 dev-libs/expat dev-util/cmake media-gfx/exiv2 media-libs/lcms media-libs/libcanberra media-libs/libiptcdata media-libs/libjpeg-turbo media-libs/libpng media-libs/tiff net-misc/curl sci-libs/fftw sys-libs/zlib x11-libs/gtk+:3

### Ubuntu

Ubuntu as of version 15.10 (Wily Werewolf) supports GTK3 so you can and
should use the `gtk3` branch. Older versions of Ubuntu either do not
support `gtk3` at all or the version of GTK3 they ship is not recent
enough (the `gtk3` branch requires a minimum GTK3 version of 3.16),
meaning you must use the `master` branch which uses GTK2.

#### Ubuntu 16.10

Use the `gtk3` branch. The dependencies below are only for the `gtk3`
branch.

    sudo apt update
    sudo apt install build-essential cmake curl git libcanberra-gtk3-dev libexiv2-dev libexpat-dev libfftw3-dev libglibmm-2.4-dev libgtk-3-dev libgtkmm-3.0-dev libiptcdata0-dev libjpeg-dev liblcms2-dev libpng-dev libsigc++-2.0-dev libtiff5-dev zlib1g-dev

#### Ubuntu 16.04 LTS and 15.10

Use the `gtk3` branch. The dependencies below are only for the `gtk3`
branch.

    sudo apt-get update
    sudo apt-get install build-essential cmake curl git libbz2-dev libcanberra-gtk3-dev libexiv2-dev libexpat-dev libfftw3-dev libglibmm-2.4-dev libgtk-3-dev libgtkmm-3.0-dev libiptcdata0-dev libjpeg8-dev liblcms2-dev libpng12-dev libsigc++-2.0-dev libtiff5-dev zlib1g-dev

#### Ubuntu 15.04, 14.10, 14.04 LTS

Use the `master` branch. The dependencies below are only for the
`master` branch.

    sudo apt-get update
    sudo apt-get install build-essential cmake curl git libbz2-dev libcanberra-gtk-dev libexiv2-dev libexpat-dev libfftw3-dev libglibmm-2.4-dev libgtk2.0-dev libgtkmm-2.4-dev libiptcdata0-dev libjpeg8-dev liblcms2-dev libpng12-dev libsigc++-2.0-dev libtiff5-dev zlib1g-dev

RawTherapee requires GCC version 4.9 or higher. Ubuntu 14.04 LTS ships
with GCC version 4.8.2 which is too old - to get 4.9, follow these
steps:
<http://askubuntu.com/questions/466651/how-do-i-use-the-latest-gcc-on-ubuntu-14-04>

#### Ubuntu 13.10, 13.04, 12.10, 12.04 LTS, 11.10

These versions of Ubuntu are badly outdated. The code below used to work
but it may stop working at any moment. Upgrade your operating system.

As these versions of Ubuntu only support GCC-4.8.1 and older, the latest
commit you will be able to compile is [commit
b343b9a7](https://github.com/Beep6581/RawTherapee/commit/b343b9a7) from
2015-12-29 - newer versions will not compile.

    sudo apt-get update
    sudo apt-get install build-essential cmake curl git libbz2-dev libcanberra-gtk-dev libexiv2-dev libexpat-dev libfftw3-dev libglibmm-2.4-dev libgtk2.0-dev libgtkmm-2.4-dev libiptcdata0-dev libjpeg8-dev liblcms2-dev libpng12-dev libsigc++-2.0-dev libtiff5-dev zlib1g-dev

#### Ubuntu 10.10 and 11.04

These versions of Ubuntu are badly outdated. The code below used to work
but it may stop working at any moment. Upgrade your operating system.

    sudo apt-add-repository ppa:dasprid/rawtherapee
    sudo apt-get update
    sudo apt-get install cmake curl git libbz2-dev libcanberra-gtk-dev libexiv2-dev libexpat-dev libglibmm-2.4-dev libgtk2.0-dev libgtkmm-2.4-dev libiptcdata0-dev libjpeg62 liblcms2-dev libnm-glib2 libpng12-dev libsigc++-2.0-dev libtiff4-dev zlib1g-dev

## Compiling: The Manual Way

This section describes compiling RawTherapee manually .

### Clone the source

First, you need to clone RawTherapee's source code repository. Bring up
your console and run this:

    git clone https://github.com/Beep6581/RawTherapee ~/repo-rt
    cd ~/repo-rt

### Choose a branch

New features and bug fixes are made on their own branches. Once tested,
those branches are merged into the "master" branch which uses GTK+ 2.
About once a week, the "master" branch is merged into the "gtk3" branch
which uses the newer and nicer GTK+ 3.

To see all available branches, type:

    git branch -a

To choose a branch, type:

    git checkout <branchname>

We recommend you use the "`gtk3`" branch if your system supports GTK+
3.16 or newer, or the "`master`" branch if it does not.

Note: compiling RawTherapee version 3, or any version older than that,
will fail on a modern system, as you will be missing the old
dependencies.

### Compile RawTherapee

Now you will make an out-of-source compilation of RawTherapee, it will
be built into the ~/repo-rt/build/release folder, and then you will move
this folder to your home directory and rename it to "rt", so make sure
there is no ~/rt folder already!

There are a few compilation settings you need to be aware of, you will
pass these to CMake using the -D option as described below:

BUILD_TYPE
You must specify the `BUILD_TYPE` when building RawTherapee. You can set
the `BUILD_TYPE` value to "`debug`" or "`release`". The "debug" build
will let you [get a useful
stack-backtrace](How_to_write_useful_bug_reports "wikilink") if
RawTherapee crashes while running through GDB which you can then submit
to us so we can find the problem and fix it, but it will not be
speed-optimized so it will run slowly. The "release" build will not
provide any useful information when it crashes, but does contain many
speed optimizations resulting in a program that works many times faster
than the "debug" version would! For normal use, go for "release". If you
find a reproducible bug, then make a "debug" build and send us a
stack-backtrace (or fix it yourself and send us the patch!).


To make a "release" type build, write: `-DCMAKE_BUILD_TYPE="release"`

Replace "release" by "debug" as needed.

<!-- -->

USE_OLD_CXX_ABI
When compiling a program, one must use the same conventions as those
used by the libraries which that program relies upon, otherwise
compilation (linking) will fail. Generally one does not need to concern
oneself with this, but we are now at a time when GCC4 is being phased
out by GCC5, each by default uses a convention incompatible with the
other, and so this issue is relevant. If the libraries on your system
have been compiled using GCC5, they probably use a standard called
C++11. This means that your RawTherapee build must use the same
standard, which is the case by default. However if despite using GCC5
your libraries were built using the older C++03 standard, then
RawTherapee must be set to use the same, and this is when you would set
"USE_OLD_CXX_ABI" to "ON":


To enable USE_OLD_CXX_ABI, write: `-DUSE_OLD_CXX_ABI="ON"`

<!-- -->

CACHE_NAME_SUFFIX
The CACHE_NAME_SUFFIX options dictates the suffix of the cache and
config folder names the compiled RawTherapee build will use.

See the [File Paths](File_Paths "wikilink") article for a full
explanation.

<!-- -->

PROC_TARGET_NUMBER
The PROC_TARGET_NUMBER option sets which CPU type to optimize for. "2"
is a safe choice because it means "native", so the optimizations will be
automatically detected for your CPU.

For more info, see the file "ProcessorTargets.cmake" in the cloned
repository.


To make a build using "native" optimizations, write:
`-DPROC_TARGET_NUMBER="2"`

Finally, you need to find out how many threads your CPU supports. This
will make compilation faster but it will have no effect on the speed of
running RawTherapee.

Threads
To find out how many threads your CPU supports, run:

`grep -c processor /proc/cpuinfo`

Then replace the number in "-j8" below with this number.

Now you are ready to compile:

    cd ~/repo-rt
    rm -rf build; make clean; ./clean
    mkdir build && cd build
    cmake -DCMAKE_CXX_FLAGS="-std=c++11 -Wno-deprecated-declarations -Wno-unused-result" \
          -DWITH_LTO="OFF" \
          -DCMAKE_BUILD_TYPE="release" \
          -DPROC_TARGET_NUMBER="2" \
          -DBUILD_BUNDLE="ON" \
          -DBINDIR="." \
          -DDATADIR="." \
          -DCACHE_NAME_SUFFIX="4" ..
    make -j8 install
    mv release ~/rt

### Run RawTherapee

To run RawTherapee:

    ~/rt/rawtherapee

The source code repository is in `~/repo-rt` and the compiled program is
in `~/rt`

You can safely delete `~/repo-rt` if you so wish. The compiled program
will still work, but then you will have to redo all the above steps if
you want to update. Rather, leave the repository intact so that you can
do the next step in a week or a month's time.

### Update RawTherapee

Every time you want to update your RawTherapee to the latest code
available, just do the following and then repeat the [Compile
RawTherapee](Linux#Compile_RawTherapee "wikilink") step above:

    cd ~/repo-rt
    git pull