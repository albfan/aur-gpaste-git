# Maintainer: Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>
# Contributor: FzerorubigD <Fzerorubigd {AT} GMail {DOT} com>
# Contributor: Ewout van Mansom <ewout@vanmansom.name>

pkgname=gpaste-git
pkgver=42.1+14+gfd41f430
pkgrel=2
pkgdesc="Clipboard management system"
url="http://www.imagination-land.org/tags/GPaste.html"
license=(GPL3)
arch=(i686 x86_64)
depends=(gtk3)
makedepends=(intltool vala appstream-glib gobject-introspection gnome-shell gnome-control-center git meson)
optdepends=("wgetpaste: Upload clipboard contents")
provides=("gpaste=$pkgver")
conflicts=(gpaste)
options=(!emptydirs)
source=("$pkgname::git+https://github.com/keruspe/gpaste.git#branch=master")
sha256sums=('SKIP')

pkgver() {
  cd $pkgname
  git describe --tags | sed 's/^v//;s/-/+/g'
}

prepare() {
  cd $pkgname
}


build() {
  arch-meson $pkgname build
  meson compile -C build
}

package() {
  meson install -C build --destdir "$pkgdir"
  install -Dt "$pkgdir/usr/share/licenses/$pkgname" -m644 $pkgname/COPYING
}
