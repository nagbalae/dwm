pkgname=dwm-git
_pkgname=dwm
pkgver=v1.0
pkgrel=1
pkgdesc="A dynamic window manager for X nagbalae version"
url="http://github.com/nagbalae/dwm"
arch=('i686' 'x86_64')
license=('MIT')
options=(zipman)
depends=('libx11' 'libxinerama' 'libxft')
makedepends=('git')
provides=('dwm')
conflicts=('dwm')
source=("$_pkgname::git+https://github.com/nagbalae/dwm"
        )
md5sums=( 'SKIP'
         )

pkgver(){
  cd $_pkgname
  #git describe --long --tags | sed -E 's/([^-]*-g)/r\1/;s/-/./g'
  echo 'v1.0'
}

prepare() {
  cd $_pkgname
  if [[ -f "$srcdir/config.h" ]]; then
    cp -fv "$srcdir/config.h" config.h
  fi
}

build() {
  cd $_pkgname
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
  cd $_pkgname
  make PREFIX=/usr DESTDIR="$pkgdir" install
  install -m644 -D LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
  install -m644 -D README.md "$pkgdir/usr/share/doc/$pkgname/README.md"
  install -m644 -D arch/dwm.desktop "$pkgdir/usr/share/xsessions/dwm.desktop"
}

# vim:set ts=2 sw=2 et:
