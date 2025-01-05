1.  Download Coverity Build Tool <https://scan.coverity.com/download>
    and extract to e.g. \$HOME/programs/
2.  cd to RawTherapee source clone:

    `cd ~/repo-rt`
3.  Clean up:

    `make clean && ./clean`
4.  Run "cov-build", either passing a script which compiles RawTherapee:

    `~/programs/cov-analysis-linux64-7.7.0.4/bin/cov-build --dir cov-int ./tools/buildRT -b`

    or by passing the compilation instructions manually, in which case
    first create the build directory, enter it and run "cmake":

    `mkdir build && cd build && cmake -DCMAKE_CXX_FLAGS="-std=c++11" -DWITH_LTO="OFF" -DCMAKE_BUILD_TYPE="release" -DPROC_TARGET_NUMBER="2" -DBUILD_BUNDLE="ON" -DBINDIR="." -DDATADIR="." ..`

    and then "cov-build" with "make":

    `~/programs/cov-analysis-linux64-7.7.0.4/bin/cov-build --dir cov-int make -j8`
5.  Create a compressed tar archive of the results (xz has the best
    compression) with "cov-int" as the root:

    `tar caf rawtherapee.xz cov-int`
6.  Upload the build to
    <https://scan.coverity.com/projects/3455/builds/new?tab=upload>