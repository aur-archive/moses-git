# Maintainer: Filip Graliński <filipg@amu.edu.pl>
pkgname=moses-git
pkgver=20121023
pkgrel=1
pkgdesc="An MT system"
arch=('i686' 'x86_64')
url="http://www.statmt.org/moses/"
license=('LGPL')
makedepends=(gcc make)
depends=(giza-pp irstlm boost-libs bash perl python xmlrpc-c)

_gitroot="https://github.com/moses-smt/mosesdecoder"
_gitname="mosesdecoder"

build() {
  cd $srcdir

  msg "Connecting to GIT server...."

  if [ -d $_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot $_gitname
  fi

  cd "$srcdir/$_gitname"

  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  ./bjam --with-xmlrpc-c --with-irstlm=/opt/irstlm --with-giza=/usr/bin debug-symbols=off --prefix="${pkgdir}/opt/moses" --install-scripts
}
