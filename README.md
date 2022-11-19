# PKGBUILD for Qt6 SVG Static Version on Msys2

Here's the Msys2 PKGBUILD for Qt6 Base, statically-linked version. Initially this is for compiling [Rui Nuno Capela](https://github.com/rncbc)'s [Vee One Suite](https://www.rncbc.org/drupal/node/2226) on my computer.

As newer versions of Vee One Suite (since `a880014f`) depend on Qt6 SVG, a static version should be useful too.

Components will be installed in a dedicated path `/opt/qt6-static/`, so that it won't interfere with Msys2's own Qt6 packages.

> **NOTICE: **
>
> **This version should be used with [my static Qt6 base package](https://github.com/AnClark/msys2-qt6base-static). **
> **It's NOT the static version of Msys2's `mingw-w64-x86_64-qt6-svg` package!**

## Prerequisites

You need to build and install [my static Qt6 base package](https://github.com/AnClark/msys2-qt6base-static) first. It's required for building any Qt6 components statically.

## Usage

1. Run Msys2 **MinGW64 shell**. 

   **DO NOT USE MSYS SHELL!** It uses Msys's POSIX-compatible compilers, which are incompatible with native Win32 environment.

2. Clone this repo. Make sure that you won't put other files in `PKGBUILD`'s directory.

```bash
git clone https://github.com/AnClark/msys2-qt6svg-static ~/msys2-qt6svg-static
```

3. Build package.

```bash
cd ~/msys2-qt6svg-static/
makepkg -f
```

When done, you'll get a package file: ```mingw-w64-x86_64-qtsvg6-static-6.x.x-x86_64.pkg.tar.zst```. `6.x.x` should be the actual Qt version.

4. Install package.

```bash
pacman -U mingw-w64-x86_64-qtsvg6-static-6.x.x-x86_64.pkg.tar.zst
```

Finally, Qt6 base static library will be installed into `/opt/qt6-static`.

## Enable Qt6 statically-linking for CMake

To build your program with static Qt6 libraries, if your project uses CMake, you can invoke it before configuring with CMake:

```bash
source /opt/qt6-static/bin/qt6-static-env.sh
```

Including this script will configure some necessary environment variables to let CMake choose static version of Qt6 library.

## Authors

- Original author: [Rui Nuno Capela (rncbc)](https://github.com/rncbc)
- Maintainer: [AnClark](https://github.com/AnClark)

## References

rncbc's official repos for Qt6 static build:

- <https://build.opensuse.org/package/show/home:rncbc/qtbase6-static> (OBSOLETE)
- <https://build.opensuse.org/project/show/home:rncbc:qt6.1-static>
- <https://build.opensuse.org/project/show/home:rncbc:qt6.2-static>
