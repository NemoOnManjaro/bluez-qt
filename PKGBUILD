# Maintainer: Antonio Rojas <arojas@archlinux.org>

pkgname=bluez-qt
pkgver=5.35.0
pkgrel=1
pkgdesc='Qt wrapper for Bluez 5 DBus API'
arch=(i686 x86_64)
url='https://community.kde.org/Frameworks'
license=(GPL2)
depends=(qt5-declarative bluez)
makedepends=(extra-cmake-modules mesa)
conflicts=(libbluedevil-frameworks)
groups=(kf5)
source=("https://download.kde.org/stable/frameworks/${pkgver%.*}/${pkgname}-${pkgver}.tar.xz"{,.sig})
sha256sums=('0f3142f59d3ec9e7e5843034401ee4fc7f091efb46f410e6ed20ac96320443b4'
            'SKIP')
validpgpkeys=(53E6B47B45CEA3E0D5B7457758D0EE648A48B3BB) # David Faure <faure@kde.org>

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../$pkgname-$pkgver \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_LIBDIR=lib \
    -DUDEV_RULES_INSTALL_DIR=/usr/lib/udev/rules.d
  make
}

package() {
  cd build
  make DESTDIR="$pkgdir" install
}
