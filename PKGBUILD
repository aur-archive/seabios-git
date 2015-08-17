# Maintainer: fredbezies <fredbezies at gmail.com>

pkgname=seabios-git
pkgver=rel.1.7.5.r125.g2c9870f
pkgrel=1
pkgdesc="A 16-bit x86 bios - git version - to be used with qemu-git"
arch=(any)
license=('GPL3' 'LGPL3')
url="http://www.coreboot.org/SeaBIOS"
makedepends=('iasl' 'python2')
source=('git://git.seabios.org/seabios.git')
options=(!strip)
md5sums=('SKIP')
provides=('seabios')
conflicts=('seabios')

_gitname="seabios"

pkgver() {
  cd "$srcdir/$_gitname"
  git describe --long --tags | sed -E 's/([^-]*-g)/r\1/;s/-/./g'
} 

build()
{
    export LC_ALL=en_US.UTF-8
    cd "${srcdir}/$_gitname"
    sed -i -e 's/python/python2/g' Makefile
    make
}

package()
{
    install -D -m644  "${srcdir}/$_gitname/out/bios.bin" "${pkgdir}/usr/share/qemu/bios.bin"
}

