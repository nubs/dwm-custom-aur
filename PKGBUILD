pkgname=dwm-nubs
_basepkgname=dwm
pkgver=6.0
pkgrel=2
pkgdesc="A dynamic window manager for X"
url="http://dwm.suckless.org"
arch=('i686' 'x86_64')
license=('MIT')
options=(zipman)
depends=('libx11' 'libxinerama')
install=dwm.install
source=(http://dl.suckless.org/dwm/dwm-$pkgver.tar.gz
	config.h
	bstack.c
	dwm.desktop)
md5sums=('8bb00d4142259beb11e13473b81c0857'
         '1d7be3c2b80649fc18f9fe1d6734394e'
         'b031a1054151e06b0119be48fd9b504d'
         '939f403a71b6e85261d09fc3412269ee')

build() {
  cd $srcdir/$_basepkgname-$pkgver
  cp $srcdir/config.h config.h
  cp $srcdir/bstack.c bstack.c
  sed -i 's/CPPFLAGS =/CPPFLAGS +=/g' config.mk
  sed -i 's/^CFLAGS = -g/#CFLAGS += -g/g' config.mk
  sed -i 's/^#CFLAGS = -std/CFLAGS += -std/g' config.mk
  sed -i 's/^LDFLAGS = -g/#LDFLAGS += -g/g' config.mk
  sed -i 's/^#LDFLAGS = -s/LDFLAGS += -s/g' config.mk
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
  cd $srcdir/$_basepkgname-$pkgver
  make PREFIX=/usr DESTDIR=$pkgdir install
  install -m644 -D LICENSE $pkgdir/usr/share/licenses/$_basepkgname/LICENSE
  install -m644 -D README $pkgdir/usr/share/doc/$_basepkgname/README
  install -m644 -D $srcdir/dwm.desktop $pkgdir/usr/share/xsessions/dwm.desktop
}
