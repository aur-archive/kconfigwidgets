# Maintainer: Andrea Scarpino <andrea@archlinux.org>

pkgname=kconfigwidgets
pkgver=4.99.0
pkgrel=1
pkgdesc='Widgets for KConfig'
arch=('i686' 'x86_64')
url='https://projects.kde.org/projects/frameworks/kconfigwidgets'
license=('LGPL')
depends=('kauth' 'kcodecs' 'kconfig' 'karchive' 'kguiaddons' 'ki18n'
         'kwidgetsaddons')
makedepends=('extra-cmake-modules' 'kdoctools')
groups=('kf5')
source=("http://download.kde.org/unstable/frameworks/${pkgver}/${pkgname}-${pkgver}.tar.xz")
md5sums=('6465152efd2962e0c8493ff0816aebfd')

prepare() {
  mkdir -p build
}

build() {
  export XDG_DATA_DIRS="/opt/kf5/share:$XDG_DATA_DIRS"

  cd build
  cmake ../${pkgname}-${pkgver} \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/opt/kf5 \
    -DLIB_INSTALL_DIR=lib \
    -DBUILD_TESTING=OFF
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
