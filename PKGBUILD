# Maintainer: Anurag Roy <anuragr9847@gmail.com>
_pkgname="st"
pkgname="$_pkgname-royarg-git"
pkgver=0.8.5.r2.7878a76
pkgrel=1
pkgdesc="A modified version of the simple virtual terminal emulator for X."
arch=('i686' 'x86_64' 'armv7h')
url="https://github.com/RoyARG02/$_pkgname"
license=('MIT')
depends=('libxft')
makedepends=('ncurses' 'libxext' 'git')
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
  make
}

package() {
  cd "$_pkgname"
  make PREFIX=/usr DESTDIR="$pkgdir/" install
  install -Dm644 README "$pkgdir"/usr/share/doc/$_pkgname/README
  install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$_pkgname/LICENSE
}
