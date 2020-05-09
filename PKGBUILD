# Maintainer: Antonio Rojas <arojas@archlinux.org>

pkgname=bluez-qt
pkgver=5.70.0
pkgrel=1
pkgdesc='Qt wrapper for Bluez 5 DBus API'
arch=(x86_64)
url='https://community.kde.org/Frameworks'
license=(GPL2)
depends=(qt5-base bluez)
makedepends=(extra-cmake-modules doxygen qt5-tools qt5-doc qt5-declarative)
optdepends=('qt5-declarative: QML bindings')
groups=(kf5)
source=("https://download.kde.org/stable/frameworks/${pkgver%.*}/$pkgname-$pkgver.tar.xz"{,.sig})
sha256sums=('33c57cff229ca9df34430eb21bab4209adb802e163b9332b06156f8f89be10cf'
            'SKIP')
validpgpkeys=(53E6B47B45CEA3E0D5B7457758D0EE648A48B3BB) # David Faure <faure@kde.org>

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../$pkgname-$pkgver \
    -DUDEV_RULES_INSTALL_DIR=/usr/lib/udev/rules.d \
    -DBUILD_TESTING=OFF \
    -DBUILD_QCH=ON
  make
}

package() {
  cd build
  make DESTDIR="$pkgdir" install
}
