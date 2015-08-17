# Maintainer: Gonzalo Jose Hernandez <GonzaloHernandez@udenar.edu.co>
# Contributor: Gonzalo Jose Hernandez <GonzaloHernandez@udenar.edu.co>
pkgname=nxt-pc-remote-control
pkgver=35
pkgrel=1
pkgdesc="Bluetooth remote control to NXT Brick"
arch=('i686' 'x86_64')
url="https://code.google.com/p/nxt-pc-remote-control"
license=('GPL')
depends=('qt5-base' 'icu' 'bluez' 'bluez-libs')
makedepends=('subversion')
provides=(nxt-pc-remote-control)
conflicts=(nxt-pc-remote-control)
source=()
md5sums=()
 
_svntrunk="https://nxt-pc-remote-control.googlecode.com/svn/trunk/"
_svnmod=nxt-pc-remote-control
 
build() {
  cd $srcdir
  msg "Connecting to SVN server...."
  if [ -d $_svnmod/.svn ]; then
    (cd $_svnmod && svn up -r $pkgver)
  else
    svn co $_svntrunk --config-dir ./ -r $pkgver $_svnmod
  fi
 
  msg "SVN checkout done or server timeout"
  msg "Starting make..."
  svn export $_svnmod $_svnmod-build
  cd $_svnmod-build
  qmake -o Makefile $srcdir/nxt-pc-remote-control/nxt-pc-remote-control.pro
  make
}
 
package() {
  mkdir -p $pkgdir/usr/bin
  mkdir -p $pkgdir/usr/share/applications
  mkdir -p $pkgdir/usr/share/icons
  install -m 755 -D $srcdir/$pkgname-build/$pkgname $pkgdir/usr/bin/
  cd ..
  install -m 755 -D $pkgname.desktop $pkgdir/usr/share/applications/
  install -m 755 -D $pkgname.png $pkgdir/usr/share/icons/  
}
