# Maintainer: AnClark Liu <clarklaw4701@gmail.com>

pkgbase=qtsvg
pkgname=mingw-w64-x86_64-${pkgbase}6-static
pkgnamesimple=${pkgbase}6-static
pkgver=6.4.2
pkgext=
pkgrel=1
pkgdesc='Qt6 classes for displaying the contents of SVG files - static libraries'
arch=('x86_64')
url='https://www.qt.io'
license=('GPL3' 'LGPL3')
depends=('mingw-w64-x86_64-qtbase6-static')
makedepends=('mingw-w64-x86_64-gcc' 'mingw-w64-x86_64-cmake' 'mingw-w64-x86_64-ninja')
conflicts=()
groups=('qt' 'qt6')
source=("https://download.qt.io/official_releases/qt/${pkgver%.*}/${pkgver}/submodules/${pkgbase}-everywhere-src-${pkgver}${pkgext}.tar.xz")
sha512sums=('SKIP')

build() {
  source /opt/qt6-static/bin/qt6-static-env.sh
  cd "${pkgbase}-everywhere-src-${pkgver}${pkgext}"

  cmake . \
   -DCMAKE_INSTALL_PREFIX=C:/opt/qt6-static \
   -DBUILD_SHARED_LIBS=OFF \
   -DCMAKE_BUILD_TYPE=Release \
   -DQT_BUILD_EXAMPLES=OFF \
   -DQT_BUILD_TESTS=OFF

  cmake --build . --parallel
}

package() {
  cd "${pkgbase}-everywhere-src-${pkgver}${pkgext}"
  DESTDIR="${pkgdir}" \
  cmake --install .
}
