# Maintainer: Antonio Rojas <arojas@archlinux.org>

pkgname=bluez-qt
pkgver=5.44.0
pkgrel=1
pkgdesc='Qt wrapper for Bluez 5 DBus API'
arch=(x86_64)
url='https://community.kde.org/Frameworks'
license=(GPL2)
depends=(qt5-declarative bluez)
makedepends=(extra-cmake-modules mesa doxygen qt5-tools)
groups=(kf5)
source=("https://download.kde.org/stable/frameworks/${pkgver%.*}/${pkgname}-${pkgver}.tar.xz"{,.sig})
sha256sums=('bb73134db489fab1adde6e6f26a4298b07a36dfb3edba1671c01f3c3e0809f14'
            'SKIP')
validpgpkeys=(53E6B47B45CEA3E0D5B7457758D0EE648A48B3BB) # David Faure <faure@kde.org>

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../$pkgname-$pkgver \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_INSTALL_LIBDIR=lib \
    -DUDEV_RULES_INSTALL_DIR=/usr/lib/udev/rules.d
  make
}

package() {
  cd build
  make DESTDIR="$pkgdir" install
}
