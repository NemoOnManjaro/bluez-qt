# Maintainer: Antonio Rojas <arojas@archlinux.org>

pkgname=bluez-qt
pkgver=5.11.0
pkgrel=1
pkgdesc='Qt wrapper for Bluez 5 DBus API'
arch=(i686 x86_64)
url='https://projects.kde.org/projects/kde/workspace/bluez-qt'
license=(GPL2)
depends=(qt5-declarative bluez)
makedepends=(extra-cmake-modules)
conflicts=(libbluedevil-frameworks)
source=("http://download.kde.org/stable/plasma/${pkgver}/$pkgname-$pkgver.tar.xz")
md5sums=('909827fc26098c7b4ab48c7228801e16')

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../$pkgname-$pkgver \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_LIBDIR=lib \
    -DKDE_INSTALL_USE_QT_SYS_PATHS=ON \
    -DUDEV_RULES_INSTALL_DIR=/usr/lib/udev/rules.d
  make
}

package() {
  cd build
  make DESTDIR="$pkgdir" install
}
