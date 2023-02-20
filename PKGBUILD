# Maintainer: Anurag Roy <anuragr9847@gmail.com>
_pkgname="st"
pkgname="$_pkgname-royarg-git"
pkgver=0.9.r4.4bc2c6e
pkgrel=1
pkgdesc="A modified version of the simple virtual terminal emulator for X."
arch=('i686' 'x86_64' 'armv7h')
url="https://github.com/RoyARG02/$_pkgname"
license=('MIT')
depends=('libxft')
makedepends=('ncurses' 'git')
optdepends=('xorg-xrdb: for loading X resources')
provides=("$_pkgname")
conflicts=("$_pkgname" "$_pkgname-git")
source=("git+$url.git")
md5sums=('SKIP')

pkgver() {
  cd "$_pkgname"
  git describe --long --tags | sed 's/\([^-]*-\)g/r\1/;s/-/./g'
}

build() {
  cd "$_pkgname"
  # Remove terminfo entries owned by ncurses
  sed '/st|/,/^$/d; /st-256color|/,/^$/d' st.info > st.info.tmp
  mv st.info.tmp st.info
  make \
    X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
  cd "$_pkgname"
  make PREFIX=/usr DESTDIR="$pkgdir" install
  install -Dm644 README "$pkgdir"/usr/share/doc/$pkgname/README
  install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}
