# libretro-64bit-rpi4
64-bit libretro cores for rpi4

Raspberry Pi OS Debian Bullseye 64-bit


Variables used in each build session
- d
- d


Retroarch
- git clone --recursive
- cd Retroarch


mupen
- make -j4 WITH_DYNAREC=aarch64 FORCE_GLES3=1 HAVE_PARALLEL_RSP=1 HAVE PARALLEL_RDP=1


paralell
- Add -DARM_FIX to the end of each export variables
- make -j4 WITH_DYNAREC=aarch64 USE_CXD4_NEW=1 USE_SSE2NEON=1 HAVE_PARALLEL=1 HAVE_OPENGL=1 FORCE_GLES=1

bsnes
- make -j4


picodrive
- ./configure
- make -j4 -f Makefile.libretro
- 




Variables set for each build (just run in same terminal window)

- export AR="gcc-ar-10.3.0"
- export CC="gcc-10.3.0"
- export CXX="g++-10.3.0"
- export CPP="cpp-10.3.0"
- export FC="gfortran-10.3.0"
- export RANLIB="gcc-ranlib-10.3.0"
- export LD="$CXX"


These cores may run in the retroarch in the debian repo

(from sudo apt install retroarch)

I never checked if it was 64-bit, but it's version 1.7 and the latest is 1.10. I just built retroarch from source. If you don't wan't to mess around with the compilations then it's worth trying to install the retroarch from the debian repo and using these cores.

```
Retroarch
```

PATH=/opt/native-pi-gcc-10.3.0-64/bin:$PATH LD_LIBRARY_PATH=/opt/native-pi-gcc-10.3.0-64/lib:$LD_LIBRARY_PATH ./configure --disable-vg --disable-opengl1 --disable-dispmanx --enable-x11 --disable-sdl2 --disable-ffmpeg --enable-udev --disable-sdl --disable-pulse --disable-freetype --disable-7zip --disable-videocore --enable-udev --enable-alsa --enable-opengles --enable-vulkan --enable-opengl --disable-caca


PATH=/opt/native-pi-gcc-10.3.0-64/bin:$PATH LD_LIBRARY_PATH=/opt/native-pi-gcc-10.3.0-64/lib:$LD_LIBRARY_PATH CFLAGS='-march=armv8-a+fp+simd -mcpu=cortex-a72  -mtune=cortex-a72 -O3' CXXFLAGS='-march=armv8-a+fp+simd -mcpu=cortex-a72  -mtune=cortex-a72 -O3' make -j4

```
SNES - snes9x2010
```

PATH=/opt/native-pi-gcc-10.3.0-64/bin:$PATH LD_LIBRARY_PATH=/opt/native-pi-gcc-10.3.0-64/lib:$LD_LIBRARY_PATH CFLAGS='-march=armv8-a+fp+simd -mcpu=cortex-a72  -mtune=cortex-a72 -O3' CXXFLAGS='-march=armv8-a+fp+simd -mcpu=cortex-a72  -mtune=cortex-a72 -O3' make -j4

```
Genesis - picodrive
```

PATH=/opt/native-pi-gcc-10.3.0-64/bin:$PATH LD_LIBRARY_PATH=/opt/native-pi-gcc-10.3.0-64/lib:$LD_LIBRARY_PATH CFLAGS='-march=armv8-a+fp+simd -mcpu=cortex-a72  -mtune=cortex-a72 -O3' CXXFLAGS='-march=armv8-a+fp+simd -mcpu=cortex-a72  -mtune=cortex-a72 -O3' make -j4

```
N64 - mupen64plus-next (nx one)
```

PATH=/opt/native-pi-gcc-10.3.0-64/bin:$PATH LD_LIBRARY_PATH=/opt/native-pi-gcc-10.3.0-64/lib:$LD_LIBRARY_PATH CFLAGS='-march=armv8-a+fp+simd -mcpu=cortex-a72  -mtune=cortex-a72 -O3' CXXFLAGS='-march=armv8-a+fp+simd -mcpu=cortex-a72  -mtune=cortex-a72 -O3' make -j4 WITH_DYNAREC=aarch64 MESA=1 GLES3=1

```
N64 - paralell64
```

PATH=/opt/native-pi-gcc-10.3.0-64/bin:$PATH LD_LIBRARY_PATH=/opt/native-pi-gcc-10.3.0-64/lib:$LD_LIBRARY_PATH CFLAGS='-march=armv8-a+fp+simd -DARM_FIX -mcpu=cortex-a72  -mtune=cortex-a72 -O3' CXXFLAGS='-march=armv8-a+fp+simd -mcpu=cortex-a72  -mtune=cortex-a72 -O3' make -j$(nproc) WITH_DYNAREC=aarch64 USE_CXD4_NEW=1 USE_SSE2NEON=1


Some of the cores will give an error during build about cannot find PATH_MAX or some other variable. Find the offending file and add
#import <linux/limits.h>
near the top and rerun build command


I can't guarantee these cores will work for you but they work for me.
