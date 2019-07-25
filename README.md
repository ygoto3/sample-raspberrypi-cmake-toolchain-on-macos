# sample-raspberrypi-cmake-toolchain-on-macos

A sample Raspberry Pi (Raspbian) CMake toolchain on macOS.

Requirement
---

- Homebrew

Usage
---

Install arm-linux-gnueabihf-binutils, llvm, and rsync via Homebrew if you have not installed these packages.

```
$ brew install arm-linux-gnueabihf-binutils llvm rsync
```

Move to your home directory, and rsync directories below from your Raspberry Pi which you need to build a toolchain for Raspbian.

```
$ cd ~
$ rsync -rzLR --safe-links pi@<raspbian_ip_address>:/usr/lib/arm-linux-gnueabihf sysroot/
$ rsync -rzLR --safe-links pi@<raspbian_ip_address>:/usr/lib/gcc/arm-linux-gnueabihf sysroot/
$ rsync -rzLR --safe-links pi@<raspbian_ip_address>:/usr/include sysroot/
$ rsync -rzLR --safe-links pi@<raspbian_ip_address>:/lib/arm-linux-gnueabihf sysroot/
```

Move back to the repository's directory, and run cmake.sh.

```
$ cd path/to/c++project
$ ./cmake.sh
```

A file named "main" is created In build directory.  Then copy it to your Raspberry Pi.

```
$ cd build
$ scp main pi@<raspbian_ip_address>:/home/pi
```
