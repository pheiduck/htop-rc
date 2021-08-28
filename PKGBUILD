# Maintainer: pheiduck <pheiduck@github.com>

# Arch Linux Credits:
# Maintainer: Christian Hesse <mail@eworm.de>
# Maintainer: Angel Velasquez <angvp@archlinux.org>
# Contributor: Eric Belanger <eric@archlinux.org>
# Contributor: Daniel J Griffiths <ghost1227@archlinux.us>

pkgname=htop
pkgver=3.1.0rc1
pkgrel=1
pkgdesc='Interactive process viewer'
arch=('x86_64')
url='https://htop.dev/'
license=('GPL')
depends=('ncurses' 'libncursesw.so' 'libnl')
makedepends=('lm_sensors')
optdepends=('lm_sensors: show cpu temperatures'
            'lsof: show files opened by a process'
            'strace: attach to a running process')
options=('!emptydirs')
source=("https://github.com/htop-dev/htop/archive/${pkgver}/${pkgname}-${pkgver}.tar.gz")
sha256sums=('SKIP')

prepare() {
  cd "$pkgname-$pkgver"

  autoreconf -fi
}

build() {
  cd "$pkgname-$pkgver"

  ./configure \
      --prefix=/usr \
      --sysconfdir=/etc \
      --enable-cgroup \
      --enable-delayacct \
      --enable-openvz \
      --enable-unicode \
      --enable-vserver

  make
}

package() {
  make -C "$pkgname-$pkgver" DESTDIR="$pkgdir" install
}
