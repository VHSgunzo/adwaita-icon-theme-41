# Maintainer: Jan Alexander Steffens (heftig) <heftig@archlinux.org>
# Contributor: Lukas Fleischer <lfleischer@archlinux.org>
# Contributor: Jan de Groot <jgc@archlinux.org>

pkgbase=adwaita-icon-theme-41
pkgname=(adwaita-icon-theme-41 adwaita-cursors-41)
pkgver=41.0
pkgrel=1
pkgdesc="GNOME standard icons v41"
url="https://gitlab.gnome.org/GNOME/adwaita-icon-theme"
arch=(any)
license=(
  CCPL:by-sa
  LGPL3
)
depends=(
  hicolor-icon-theme
  gtk-update-icon-cache
  librsvg
)
makedepends=(
  git
  gtk3
)
_commit=8670d0eb2414c1ac16d927da5d1a22142ba5e346  # tags/41.0^0
source=("git+https://gitlab.gnome.org/GNOME/adwaita-icon-theme.git#commit=$_commit")
b2sums=('SKIP')

pkgver() {
  cd adwaita-icon-theme
  git describe --tags | sed 's/[^-]*-g/r&/;s/-/+/g'
}

prepare() {
  cd adwaita-icon-theme
  autoreconf -fvi
}

build() {
  cd adwaita-icon-theme
  ./configure --prefix=/usr
  make
}

check() {
  cd adwaita-icon-theme
  make check
}

package_adwaita-icon-theme-41() {
  depends+=(adwaita-cursors-41)
  conflicts=('adwaita-icon-theme')
  provides=('adwaita-icon-theme')

  make -C adwaita-icon-theme DESTDIR="$pkgdir" install

  mkdir -p cursors/usr/share/icons/Adwaita
  mv {"$pkgdir",cursors}/usr/share/icons/Adwaita/cursors
}

package_adwaita-cursors-41() {
  pkgdesc="GNOME standard cursors v41"
  conflicts=('adwaita-cursors')
  provides=('adwaita-cursors')
  depends=()

  mv cursors/* "$pkgdir"
}

# vim:set sw=2 sts=-1 et:
