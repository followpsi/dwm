# $Id$
# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Dag Odenhall <dag.odenhall@gmail.com>
# Contributor: Grigorios Bouzakis <grbzks@gmail.com>

pkgname=dwm
pkgver=6.1
pkgrel=3
pkgdesc="A dynamic window manager for X"
url="http://dwm.suckless.org"
arch=('i686' 'x86_64')
license=('MIT')
options=(zipman)
depends=('libx11' 'libxinerama' 'libxft' 'freetype2' 'st' 'dmenu')
install=dwm.install
source=(http://dl.suckless.org/dwm/dwm-$pkgver.tar.gz
	config.h
	dwm.desktop
	http://dwm.suckless.org/patches/dwm-pertag-6.1.diff)
md5sums=('f0b6b1093b7207f89c2a90b848c008ec'
         'e7163ff3b4652a21c022713a3d106531'
         '939f403a71b6e85261d09fc3412269ee'
         '3126263695676ffa7ab7d90e49bd77cb')

prepare() {
  cd "$srcdir"/$pkgname-$pkgver
  cp "$srcdir"/config.h config.h
  patch < ../dwm-pertag-6.1.diff
}

build() {
  cd "$srcdir"/$pkgname-$pkgver
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11 FREETYPEINC=/usr/include/freetype2
}

package() {
  cd "$srcdir"/$pkgname-$pkgver
  make PREFIX=/usr DESTDIR="$pkgdir" install
  install -m644 -D LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
  install -m644 -D README "$pkgdir"/usr/share/doc/$pkgname/README
  install -m644 -D "$srcdir"/dwm.desktop "$pkgdir"/usr/share/xsessions/dwm.desktop
}
