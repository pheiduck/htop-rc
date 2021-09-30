# Maintainer: pheiduck <pheiduck@github.com>

# Arch Linux Credits:
# Maintainer: Christian Hesse <mail@eworm.de>
# Maintainer: Angel Velasquez <angvp@archlinux.org>
# Contributor: Eric Belanger <eric@archlinux.org>
# Contributor: Daniel J Griffiths <ghost1227@archlinux.us>

pkgname=htop
pkgver=3.1.1
pkgrel=1
pkgdesc='Interactive process viewer'
arch=('x86_64')
url='https://htop.dev/'
_commit=d23627fda9878f0a8640c24d95145d56882ba503
license=('GPL')
depends=('ncurses' 'libncursesw.so' 'libnl')
makedepends=('git' 'lm_sensors')
optdepends=('lm_sensors: show cpu temperatures'
            'lsof: show files opened by a process'
            'strace: attach to a running process')
options=('!emptydirs')
source=("git+https://github.com/htop-dev/htop.git#commit=$_commit")
sha256sums=('SKIP')

prepare() {
  cd "$pkgname"

  autoreconf -fi
}

build() {
  cd "$pkgname"

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
  make -C "$pkgname" DESTDIR="$pkgdir" install
}
