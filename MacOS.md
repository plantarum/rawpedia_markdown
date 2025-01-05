This page details instructions for compiling RawTherapee on **Mac OS X**
systems. There are also separate pages with instructions for compiling
on [Linux](Linux "wikilink") and [Windows](Windows "wikilink"). This
guide details the **what** and **how** parts of compilation. For the
**why** and explanations of these commands, for a list of dependencies,
CMake options and other information, please refer to the detailed
[Linux](Linux "wikilink") article.

When in doubt, [join us on IRC](IRC "wikilink") and ask a human!

For instructions on cloning the source, choosing branches, configuring
CMake and doing the actual compilation, see these sections in the
[Linux](Linux "wikilink") guide. The information below is in addition to
that.

## Dependencies

See the list of dependencies in the [Compiling in
Linux](Linux#Dependencies "wikilink") article.

Additionally, you need these:

- XCode Development Tools. You only need a subset of these, but it is
  probably easier to just install all of them.
- MacPorts
- Git


Install Git:


`sudo port install git`

- Configure variants.conf


Add the following line to /opt/local/etc/macports/variants.conf:


`+no_gnome +no_x11 +quartz -x11`

- Dependencies


To install the dependencies, run:


`sudo port install cairo clang-3.7 +openmp cmake fftw-3-single gdk-pixbuf2 gtk2 gtk-engines2 gtkmm gtk-osx-application-gtk2 lcms2 libiptcdata libsigcxx2 pango`

We recommend using the latest stable version of the Clang compiler with
OpenMP support. Unstable versions are not recommended. The line above
includes it.

### libiconv patch

libiconv.2.dylib must be patched, otherwise RawTherapee will crash on
startup. The patch is available in
[\`tools/osx/libiconv_1.14_rt.patch\`](https://github.com/Beep6581/RawTherapee/blob/master/tools/osx/libiconv_1.14_rt.patch)

libiconv patching and compilation instructions:

    wget http://ftp.gnu.org/pub/gnu/libiconv/libiconv-1.14.tar.gz
    tar xf libiconv-1.14.tar.gz
    cd libiconv-1.14
    wget https://raw.githubusercontent.com/Beep6581/RawTherapee/master/tools/osx/libiconv_1.14_rt.patch
    patch -p1 < libiconv_1.14_rt.patch
    mkdir build
    cd build
    buildDir="$(pwd)"
    ../configure --prefix=/opt/local --disable-static 'CFLAGS=-arch x86_64 -mmacosx-version-min=10.5' 'LDFLAGS=-arch x86_64 -mmacosx-version-min=10.5' CXXFLAGS="-arch x86_64 -mmacosx-version-min=10.5"
    make
    make DESTDIR="$buildDir" install
    cd /opt/local/lib
    sudo cp ./libiconv.2.dylib ./libiconv.2.dylib.backup # backup MacPorts dylib
    sudo cp "${buildDir}/opt/local/lib/libiconv.2.dylib" /opt/local/lib/libiconv.2.dylib

## Compiling

See the [Compiling in Linux](Linux#Compiling:_The_Manual_Way "wikilink")
article for instructions on how to **clone** the source code, choose a
**branch** and how to configure **CMake**. Ignore the "Now you are ready
to compile" code on that page and follow the code on this page.

If you want to upload a build or otherwise share it with others, you
must use


`-DPROC_TARGET_NUMBER="1"`

and set the processor label manually by setting


`-DPROC_LABEL="generic processor"`

If you want to compile for yourself only, then use


`-DPROC_TARGET_NUMBER="2"`

and then the processor label would be irrelevant, you could skip it.

### Compile RawTherapee

Now you are ready to compile:

    cd ~/repo-rt
    rm -rf build; make clean; ./clean
    mkdir build && cd build
    cmake -DCMAKE_BUILD_TYPE="release" \
          -DPROC_TARGET_NUMBER="1" \
          -DPROC_LABEL="generic processor" \
          -DCACHE_NAME_SUFFIX="4" \
          -DCMAKE_C_COMPILER="clang-mp-3.7" \
          -DCMAKE_CXX_COMPILER="clang++-mp-3.7" \
          -DCMAKE_CXX_FLAGS="-w" \
          ..
    make -j8 install
    make macosx_bundle

### Run and Share RawTherapee

You will find a disk image in the build directory; this is the
distribution release and can be run on any machine which meets the
architecture requirements you specified in variants.conf earlier.

To provide the RawTherapee project with your build, please zip the .dmg
and AboutThisBuild.txt files together. Name the zip file according to
this template:


RawTherapee_OSX_**<OS X version>**_64_**<RawTherapee version and branch>**.zip

for example if your build is made for OS X 10.11 and the version of
RawTherapee is 4.2.789 and the branch is \`gtk3\`, name it:


RawTherapee_OSX_10.11_64_4.2.789_gtk3.zip

Upload the zip archive to <http://filebin.net/> and [open a new issue on
our GitHub page](https://github.com/Beep6581/RawTherapee/issues/new)
with the link so that we can upload it to the website.