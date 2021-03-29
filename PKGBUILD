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
makedepends=('intltool' 'gnome-common' 'libv4l')
source=($pkgname-$pkgver.tar.gz::$url/archive/refs/tags/${pkgver}.tar.gz
		01-Update-to-gettext-0.20.patch
		02-Fix-compilation-with-gcc10-fno-commo.patch)
md5sums=('d64369337a436806da9134f36ce4f449'
		 '841345e0ca89f154be724542bef44860'
		 '44116060fa3591e800c4fd8589d04795')

prepare() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  patch -Np1 -i ../01-Update-to-gettext-0.20.patch
  patch -Np1 -i ../02-Fix-compilation-with-gcc10-fno-commo.patch
}

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
