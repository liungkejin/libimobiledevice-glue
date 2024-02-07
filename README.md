# libimobiledevice-glue

Library with common code used by the libraries and tools around the
**libimobiledevice** project.

![](https://github.com/libimobiledevice/libimobiledevice-glue/workflows/build/badge.svg)

## Features

The main functionality provided by this library are **socket** helper
functions and a platform independent **thread/mutex** implementation.
Besides that it comes with a number of string, file, and plist helper
functions, as well as some other commonly used code that was originally
duplicated in the dedicated projects.

Test on Linux, macOS, Windows.

## Projects using this library

- [libusbmuxd](https://github.com/libimobiledevice/libusbmuxd)
- [libimobiledevice](https://github.com/libimobiledevice/libimobiledevice)
- [usbmuxd](https://github.com/libimobiledevice/usbmuxd)
- [libirecovery](https://github.com/libimobiledevice/libirecovery)
- [idevicerestore](https://github.com/libimobiledevice/idevicerestore)

## Installation / Getting started

Project dependcies:

* libplist

### Windows

First install [MSYS2](https://www.msys2.org/).

Then open MSYS2 MINGW32 (or MSYS2 MINGW64 if your want to build for x64).

Install all required dependencies and build tools

```shell
# for x86
pacman -S mingw-w64-i686-toolchain 
pacman -S --needed base-devel msys2-devel
pacman -S git mingw-w64-i686-cython0 mingw-w64-i686-libzip
pacman -S make automake autoconf libtool pkgconf openssl openssl-devel
```

Then clone the actual project repository:
```shell
git clone https://github.com/liungkejin/libimobiledevice-glue.git
cd libimobiledevice-glue
```

Now you can build and install it:
```shell
./autogen.sh
make
make install
```

If you require a custom prefix or other option being passed to `./configure`
you can pass them directly to `./autogen.sh` like this:
```bash
./autogen.sh --prefix=/opt/local
make
make install
```

You can find the dll file in `%MSYS2 INSTALL PATH%\mingw32\bin`
If you want use this dll in Visual Studio C++ Project, you need use `pexports.exe`
to generate .lib file

```shell
pexports.exe -v libxxx.dll > libxxx.def
```

Then open `x86 Native Tools Command Prompt` or `x64 Native Tools Command Prompt`

run
```shell
lib /DEF:libxxx.def
```

Then you can use this libxxx.lib file in C++ project

```c++
#pragma comment(lib, "libxxx.lib")
```

### Debian / Ubuntu Linux

First install all required dependencies and build tools:
```shell
sudo apt-get install \
	build-essential \
	pkg-config \
	checkinstall \
	git \
	autoconf \
	automake \
	libtool-bin \
	libplist-dev
```

Then clone the actual project repository:
```shell
git clone https://github.com/libimobiledevice/libimobiledevice-glue.git
cd libimobiledevice-glue
```

Now you can build and install it:
```shell
./autogen.sh
make
sudo make install
```

If you require a custom prefix or other option being passed to `./configure`
you can pass them directly to `./autogen.sh` like this:
```bash
./autogen.sh --prefix=/opt/local
make
sudo make install
```

## Usage

This library is directly used by libusbmuxd, libimobiledevice, etc., so there
is no need to do anything in particular.

## Contributing

We welcome contributions from anyone and are grateful for every pull request!

If you'd like to contribute, please fork the `master` branch, change, commit and
send a pull request for review. Once approved it can be merged into the main
code base.

If you plan to contribute larger changes or a major refactoring, please create a
ticket first to discuss the idea upfront to ensure less effort for everyone.

Please make sure your contribution adheres to:
* Try to follow the code style of the project
* Commit messages should describe the change well without being too short
* Try to split larger changes into individual commits of a common domain

## Links

* Homepage: https://libimobiledevice.org/
* Repository: https://git.libimobiledevice.org/libimobiledevice-glue.git
* Repository (Mirror): https://github.com/libimobiledevice/libimobiledevice-glue.git
* Issue Tracker: https://github.com/libimobiledevice/libimobiledevice-glue/issues
* Mailing List: https://lists.libimobiledevice.org/mailman/listinfo/libimobiledevice-devel
* Twitter: https://twitter.com/libimobiledev

## License

This library and utilities are licensed under the [GNU Lesser General Public License v2.1](https://www.gnu.org/licenses/lgpl-2.1.en.html),
also included in the repository in the `COPYING` file.

## Credits

Apple, iPhone, iPad, iPod, iPod Touch, Apple TV, Apple Watch, Mac, iOS,
iPadOS, tvOS, watchOS, and macOS are trademarks of Apple Inc.

This project is an independent software and has not been authorized, sponsored,
or otherwise approved by Apple Inc.

README Updated on: 2022-04-04
