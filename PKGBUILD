# Maintainer: spider-mario <spidermario@free.fr>
# Contributor: Daniel Ehlers <danielehlers@mindeye.net>
pkgname=coinor-cgl
pkgver=0.58.10
pkgrel=1
pkgdesc="COIN-OR Cut Generation Library"
arch=('i686' 'x86_64')
url="https://projects.coin-or.org/Cgl"
license=('EPL')
groups=('coinor')
depends=('coinor-clp')
source=("http://www.coin-or.org/download/source/Cgl/Cgl-${pkgver}.tgz")
sha1sums=('65856a2c9b000bb35103bdada3dba73b1cbd0b0f')

build() {
  cd Cgl-$pkgver
  COIN_SKIP_PROJECTS="Sample" \
  ./configure --prefix=/usr \
              --with-osi-lib="$(pkg-config --libs osi)" \
              --with-osi-incdir="/usr/include/coin/" \
              --with-clp-lib="$(pkg-config --libs clp)" \
              --with-clp-incdir="/usr/include/coin/" \
              --with-coinutils-lib="$(pkg-config --libs coinutils)" \
              --with-coinutils-incdir="/usr/include/coin/" -C
  make
}

check() {
  cd Cgl-$pkgver
  make test
}

package() {
  cd Cgl-$pkgver
  PKG_CONFIG_LIBDIR="$pkgdir"/usr/lib/pkgconfig/ \
  make DESTDIR="$pkgdir"/ install
}
