# Maintainer: pheiduck <pheiduck@github.com>

# Arch Linux Credits:
# Maintainer: Christian Hesse <mail@eworm.de>
# Maintainer: Angel Velasquez <angvp@archlinux.org>
# Contributor: Eric Belanger <eric@archlinux.org>
# Contributor: Daniel J Griffiths <ghost1227@archlinux.us>

pkgname=htop
pkgver=3.2.0
pkgrel=7
pkgdesc='Interactive process viewer'
arch=('x86_64')
url='https://htop.dev/'
_commit=b45eaf2fe16fb0e94333ab848962892b48648a28
license=('GPL')
depends=('libcap' 'libcap.so' 'libnl' 'ncurses' 'libncursesw.so')
makedepends=('git' 'lm_sensors')
optdepends=('lm_sensors: show cpu temperatures'
            'lsof: show files opened by a process'
            'strace: attach to a running process')
options=('!emptydirs')
validpgpkeys=('F7ABE8761E6FE68638E6283AFE0842EE36DD8C0C') # Nathan Scott <nathans@debian.org>
source=("git+https://github.com/$pkgname-dev/$pkgname.git#commit=$_commit")
sha256sums=('SKIP')

prepare() {
  cd "${pkgname}"

  autoreconf -fi
}

build() {
  cd "${pkgname}"

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
  cd "${pkgname}"

  make DESTDIR="${pkgdir}" install
}
