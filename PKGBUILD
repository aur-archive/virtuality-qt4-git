# Maintainer : Cazimi <gorheledion at gmail dot com>
pkgname=('virtuality-qt4-git')
pkgver=r110.22ba423
pkgrel=2
pkgdesc='qt4 widget style'
arch=('i686' 'x86_64')
url='https://github.com/luebking/virtuality'
license=('GPL2')
makedepends=('cmake' 'automoc4' 'git')
optdepends=('kdebase-workspace')
source=('git://github.com/luebking/virtuality.git')
md5sums=('SKIP')

pkgver() {
  cd virtuality
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}
build() {
  cd virtuality
  mkdir -p build4
  cd build4
  cmake .. -DCMAKE_BUILD_TYPE=Release  \
	       -DCMAKE_INSTALL_PREFIX=/usr \
		   -DWITH_QT5=OFF ..	 
  make
}

package() {
  depends=('qt4')
  cd virtuality/build4
  make DESTDIR="$pkgdir" install
  mv "${pkgdir}"/usr/bin/virtuality "${pkgdir}"/usr/bin/virtuality-qt4
}
