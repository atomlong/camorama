# Maintainer: Steffen Weber <-boenki-gmx-de->
# Contributor: Andrea Scarpino <bash.lnx@gmail.com>
# Contributor: Federico Quagliata (quaqo) <quaqo@despammed.com>

pkgname=camorama
pkgver=0.20.7
pkgrel=1
pkgdesc="Webcam application featuring various image filters"
url="https://github.com/alessio/camorama"
arch=('x86_64' 'arm' 'armv6h' 'armv7h' 'aarch64')
license=('GPL2')
depends=('libgnomeui')
makedepends=('intltool')
source=($pkgname-$pkgver.tar.gz::$url/archive/refs/tags/${pkgver}.tar.gz)
md5sums=('d64369337a436806da9134f36ce4f449')

build() {
  cd "$pkgname-${pkgver}"
  sh ./autogen.sh
  ./configure --prefix=/usr --sysconfdir=/usr/share
  make
}

check() {
  cd "$pkgname-${pkgver}"
  make check
}

package() {
  cd "$pkgname-${pkgver}"
  make DESTDIR="$pkgdir" install
}
