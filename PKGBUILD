# Maintainer: Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>
# Contributor: FzerorubigD <Fzerorubigd {AT} GMail {DOT} com>
# Contributor: Ewout van Mansom <ewout@vanmansom.name>

pkgname=gpaste-git
pkgver=42.1+14+gfd41f430
pkgrel=1
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

build() {
  cd $pkgname
  mkdir builddir
  cd builddir
  meson \
    --prefix='/usr' ..
  ninja
}

package() {
  cd $pkgname
  cd builddir
  DESTDIR="$pkgdir" ninja install
}
