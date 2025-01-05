This is the command used to build \`5.10-rc1\`

Intel \`x86_64\`:

    cmake -DCMAKE_BUILD_TYPE="Release" \
    -DCMAKE_OSX_ARCHITECTURES=x86_64 \
    -DCMAKE_OSX_DEPLOYMENT_TARGET=11.3 \
    -DPROC_TARGET_NUMBER="11" \
    -DPROC_LABEL="nehalem-westemere" \
    -DCACHE_NAME_SUFFIX="5-rc1" \
    -DCMAKE_C_COMPILER="clang" \
    -DCMAKE_CXX_COMPILER="clang++" \
    -DWITH_LTO="ON" \
    -DCMAKE_OSX_SYSROOT="/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX11.3.sdk" \
    -DCMAKE_OSX_DEPLOYMENT_TARGET="11.3" \
    -DLOCAL_PREFIX:STRING="/usr/local" \
    -DLENSFUNDBDIR="/Applications/RawTherapee.app/Contents/Resources/share/lensfun" \
    -DCODESIGNID:STRING="Developer ID Application: Doctor Who (ABCDE12345)" \
    -DNOTARY:STRING="--apple-id drwho@bbc.uk --team-id ABCDE12345 --password abcd-efgh-ijkl-mnop" \
    -DCMAKE_CXX_FLAGS_RELEASE="-I/usr/local/include -I/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX11.3.sdk/usr/include -Wno-pass-failed -Wno-deprecated-register -Wno-unused-command-line-argument -std=c++11 -DNDEBUG=1 -O3" \
    -DCMAKE_C_FLAGS_RELEASE="-I/usr/local/include -I/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX11.3.sdk/usr/include -Wno-pass-failed -Wno-deprecated-register -Wno-unused-command-line-argument" \
    -DCMAKE_EXE_LINKER_FLAGS="-L/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX11.3.sdk/usr/lib -Wl,-undefined,dynamic_lookup -Wl,-headerpad_max_install_names -isysroot /Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX11.3.sdk -O3 -DNDEBUG=1" \
    -DOpenMP_C_FLAGS="-fopenmp=lomp" \
    -DOpenMP_CXX_FLAGS=-fopenmp=lomp -DOpenMP_C_LIB_NAMES="libomp" \
    -DOpenMP_CXX_LIB_NAMES="libomp" \
    -DOpenMP_libomp_LIBRARY="/usr/local/opt/libomp/lib/libomp.dylib" \
    -DOpenMP_CXX_FLAGS="-Xpreprocessor -fopenmp /usr/local/opt/libomp/lib/libomp.dylib -I/usr/local/opt/libomp/include" \
    -DOpenMP_CXX_LIB_NAMES="libomp" \
    -DOpenMP_C_FLAGS="-Xpreprocessor -fopenmp /usr/local/opt/libomp/lib/libomp.dylib -I/usr/local/opt/local/include" \
    -DCMAKE_VERBOSE_MAKEFILE:BOOL=ON \
    -DOSX_NIGHTLY:BOOL=ON ..
    make -j8 install
    sudo make macosx_bundle

Universal & Apple Silicon \`arm_64\`:

    cmake -DCMAKE_BUILD_TYPE="Release" \
    -DCMAKE_OSX_ARCHITECTURES=arm64 \
    -DCMAKE_OSX_DEPLOYMENT_TARGET=13.3 \
    -DPROC_TARGET_NUMBER="2" -DPROC_LABEL="arm64" \
    -DCACHE_NAME_SUFFIX="5-rc1" \
    -DCMAKE_C_COMPILER="/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/clang" \
    -DCMAKE_CXX_COMPILER="/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/clang++" \
    -DWITH_LTO="ON" \
    -DCMAKE_OSX_SYSROOT="/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX13.3.sdk" \
    -DCMAKE_OSX_DEPLOYMENT_TARGET="13.3" -DLOCAL_PREFIX:STRING="/opt/homebrew" \
    -DLENSFUNDBDIR="/Applications/RawTherapee.app/Contents/Resources/share/lensfun" \
    -DCODESIGNID:STRING="Developer ID Application: Doctor Who (ABCDE12345)" \
    -DNOTARY:STRING="--apple-id drwho@bbc.uk --team-id ABCDE12345 --password abcd-efgh-ijkl-mnop" \
    -DCMAKE_CXX_FLAGS_RELEASE="-O3 -DNDEBUG=1 -I/opt/homebrew/include -I/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX13.3.sdk/usr/include -Wno-pass-failed -arch arm64 -Wno-deprecated-register -Wno-unused-command-line-argument -std=c++11" \
    -DCMAKE_C_FLAGS_RELEASE="-O3 -DNDEBUG=1 -I/opt/homebrew/include -I/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX13.3.sdk/usr/include -Wno-pass-failed -arch arm64 -Wno-deprecated-register -Wno-unused-command-line-argument" \
    -DCMAKE_EXE_LINKER_FLAGS="-L/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX13.3.sdk/usr/lib -Wl,-headerpad_max_install_names -isysroot /Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX13.3.sdk -arch arm64" \
    -DOpenMP_C_FLAGS="-fopenmp=lomp" -DOpenMP_CXX_FLAGS=-fopenmp=lomp -DOpenMP_C_LIB_NAMES="libomp" \
    -DOpenMP_CXX_LIB_NAMES="libomp" -DOpenMP_libomp_LIBRARY="/opt/homebrew/lib/libomp.dylib" \
    -DOpenMP_CXX_FLAGS="-Xpreprocessor -fopenmp /opt/homebrew/lib/libomp.dylib -I/opt/homebrew/include" \
    -DOpenMP_CXX_LIB_NAMES="libomp" \
    -DOpenMP_C_FLAGS="-Xpreprocessor -fopenmp /opt/homebrew/lib/libomp.dylib -I/opt/homebrew/include" \
    -DCMAKE_VERBOSE_MAKEFILE:BOOL=ON \
    -DFANCY_DMG=ON \
    -DOSX_UNIVERSAL:BOOL=ON \
    -DOSX_UNIVERSAL_URL=file:///Volumes/Public/RawTherapee_macOS_x86_64_latest.zip  \
    ..
    make -j8 install
    sudo make macosx_bundle