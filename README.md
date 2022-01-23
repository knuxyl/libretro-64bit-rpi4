# libretro-64bit-rpi4
64-bit libretro cores for rpi4

Raspberry Pi OS Debian Bullseye 64-bit

----Export variables

export CFLAGS='-march=armv8-a+fp+simd+sb+predres+crypto+crc -mcpu=cortex-a72 -mtune=cortex-a72 -O3 -funsafe-math-optimizations'

export CXXFLAGS='-march=armv8-a+fp+simd+sb+predres+crypto+crc -mcpu=cortex-a72 -mtune=cortex-a72 -O3 -funsafe-math-optimizations'


----RetroArch

git clone --recursive https://github.com/libretro/RetroArch

cd RetroArch

./configure --disable-vg --disable-opengl1 --disable-dispmanx --enable-x11 --enable-sdl2 --enable-ffmpeg --enable-udev --disable-sdl --enable-pulse --enable-freetype --enable-7zip --disable-videocore --enable-udev --enable-alsa --enable-opengles --enable-vulkan --enable-opengl --disable-caca

make -j4


----N64 (mupen)

git clone --recursive https://github.com/libretro/mupen64plus-libretro-nx

cd mupen64plus-libretro-nx

make -j4 WITH_DYNAREC=aarch64 FORCE_GLES3=1 HAVE_PARALLEL_RSP=1 HAVE_PARALLEL_RDP=1


----N64 (paralell)

Add -DARM_FIX to end of export variables

git clone --recursive https://github.com/libretro/parallel-n64

cd parallel-n64

make -j4 WITH_DYNAREC=aarch64 USE_CXD4_NEW=1 USE_SSE2NEON=1 HAVE_PARALLEL=1 HAVE_OPENGL=1 FORCE_GLES=1


----SNES (bsnes)

git clone --recursive https://github.com/libretro/bsnes-libretro

cd bsnes-libretro

make -j4


----Genesis/MD/32x (picodrive)

git clone --recursive https://git.libretro.com/libretro/picodrive

cd picodrive

./configure

make -j4 -f Makefile.libretro


----PS1 (pcsx-rearmed) (needs bios)

Add -fPIC to end of export variables

git clone --recursive https://git.libretro.com/libretro/pcsx_rearmed/

cd pcsx_rearmed/frontend

git clone --recursive https://github.com/notaz/libpicofe

cd ../../

./configure

make -f Makefile.libretro -j4


---Gamecube/Wii (dolphin) gl only (terribly slow)

git clone --recursive https://github.com/libretro/dolphin

cd dolphin

mkdir build

cd build

cmake ../ -DLIBRETRO=ON -DUSE_DISCORD_PRESENCE=OFF

make -j4


----Dreamcast (flycast) vulkan only (needs bios)

Add -DUSE_GLES -DUSE_VULKAN -DUSE_OPENGL to end of export variables

git clone --recursive https://github.com/flyinghead/flycast

cd flycast

mkdir build

cd build










