# libretro-64bit-rpi4
64-bit libretro cores for rpi4

GCC aarch64 compiler used to compile retroarch and cores (installed to /opt/)
https://github.com/abhiTronix/raspberry-pi-cross-compilers

Variables set for each build (just run in same terminal window)

export AR="gcc-ar-10.3.0"

export CC="gcc-10.3.0"

export CXX="g++-10.3.0"

export CPP="cpp-10.3.0"

export FC="gfortran-10.3.0"

export RANLIB="gcc-ranlib-10.3.0"

export LD="$CXX"


Retroarch


PATH=/opt/native-pi-gcc-10.3.0-64/bin:$PATH LD_LIBRARY_PATH=/opt/native-pi-gcc-10.3.0-64/lib:$LD_LIBRARY_PATH ./configure --disable-vg --disable-opengl1 --disable-dispmanx --enable-x11 --disable-sdl2 --disable-ffmpeg --enable-udev --disable-sdl --disable-pulse --disable-freetype --disable-7zip --disable-videocore --enable-udev --enable-alsa --enable-opengles --enable-vulkan --enable-opengl --disable-caca


PATH=/opt/native-pi-gcc-10.3.0-64/bin:$PATH LD_LIBRARY_PATH=/opt/native-pi-gcc-10.3.0-64/lib:$LD_LIBRARY_PATH CFLAGS='-march=armv8-a+fp+simd -mcpu=cortex-a72  -mtune=cortex-a72 -O3' CXXFLAGS='-march=armv8-a+fp+simd -mcpu=cortex-a72  -mtune=cortex-a72 -O3' make -j4


SNES


PATH=/opt/native-pi-gcc-10.3.0-64/bin:$PATH LD_LIBRARY_PATH=/opt/native-pi-gcc-10.3.0-64/lib:$LD_LIBRARY_PATH CFLAGS='-march=armv8-a+fp+simd -mcpu=cortex-a72  -mtune=cortex-a72 -O3' CXXFLAGS='-march=armv8-a+fp+simd -mcpu=cortex-a72  -mtune=cortex-a72 -O3' make -j4


Genesis


PATH=/opt/native-pi-gcc-10.3.0-64/bin:$PATH LD_LIBRARY_PATH=/opt/native-pi-gcc-10.3.0-64/lib:$LD_LIBRARY_PATH CFLAGS='-march=armv8-a+fp+simd -mcpu=cortex-a72  -mtune=cortex-a72 -O3' CXXFLAGS='-march=armv8-a+fp+simd -mcpu=cortex-a72  -mtune=cortex-a72 -O3' make -j4


Mupen64Plus-Next


PATH=/opt/native-pi-gcc-10.3.0-64/bin:$PATH LD_LIBRARY_PATH=/opt/native-pi-gcc-10.3.0-64/lib:$LD_LIBRARY_PATH CFLAGS='-march=armv8-a+fp+simd -mcpu=cortex-a72  -mtune=cortex-a72 -O3' CXXFLAGS='-march=armv8-a+fp+simd -mcpu=cortex-a72  -mtune=cortex-a72 -O3' make -j4 WITH_DYNAREC=aarch64 MESA=1 GLES3=1


Paralell64


PATH=/opt/native-pi-gcc-10.3.0-64/bin:$PATH LD_LIBRARY_PATH=/opt/native-pi-gcc-10.3.0-64/lib:$LD_LIBRARY_PATH CFLAGS='-march=armv8-a+fp+simd -DARM_FIX -mcpu=cortex-a72  -mtune=cortex-a72 -O3' CXXFLAGS='-march=armv8-a+fp+simd -mcpu=cortex-a72  -mtune=cortex-a72 -O3' make -j$(nproc) WITH_DYNAREC=aarch64 USE_CXD4_NEW=1 USE_SSE2NEON=1


Some of the cores will give an error during build about cannot find PATH_MAX or some other variable. Find the offending file and add
#import <linux/limits.h>
near the top and rerun build command


I can't guarantee these cores will work for you but they work for me.
