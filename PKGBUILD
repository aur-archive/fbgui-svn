# Maintainer: Gimmeapill <gimmeapill[at]gmail[dot]com>

pkgname=fbgui-svn
pkgver=80
pkgrel=1
pkgdesc="GUI library for Armstrong"
url="http://batman.no/gui2/"
arch=('x86_64' 'i686')
license=('LPGL')
depends=('armstrong-svn' 'sdl' 'freetype2')
optdepends=()
makedepends=('subversion')
provides=(fbgui)
conflicts=()
replaces=()
backup=()
install=
source=()
md5sums=()

_svntrunk="svn://anders-e.com/fbgui/trunk/fbgui"
_svnmod="fbgui"


build() {

  msg "Starting SVN checkout..."
  cd ${srcdir}
    if [ -d $_svnmod/.svn ]; then
      (cd $_svnmod && svn up -r $pkgver)
    else
      svn co $_svntrunk --config-dir ./ -r $pkgver $_svnmod
    fi
  msg "SVN checkout done or server timeout"

  cd ${srcdir}/$_svnmod
  autoreconf -vi
  ./configure --prefix=/usr
  make
    
}

package() {
  cd ${srcdir}/$_svnmod
  make DESTDIR="$pkgdir" install
}

