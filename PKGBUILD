# Maintainer: Fabio 'Lolix' Loli <fabio.loli@disroot.org> -> https://github.com/FabioLolix

pkgname=roundedsbe-git
pkgver=r232.6f75936
pkgrel=1
pkgdesc="Kwin Window Decoration with Round corners and outline effect for KWin"
arch=(x86_64)
url="https://github.com/a-parhom/RoundedSBE"
license=(GPL3)
depends=('qt5-x11extras' 'qt5-xmlpatterns' 'qt5-tools' 'kconfig' 'kconfigwidgets' 'ki18n' 'kcoreaddons' 'kcrash' 'kio' 'kservice' 'kinit' 'knotifications' 'kwin' 'kwidgetsaddons' 'kwindowsystem' 'kguiaddons' 'kglobalaccel' 'kde-dev-utils')
makedepends=('git' 'extra-cmake-modules')
provides=('roundedsbe')
conflicts=('roundedsbe')
source=("git+${url}.git")
sha256sums=('SKIP')

pkgver() {
cd RoundedSBE
( set -o pipefail
git describe --long 2>/dev/null | sed 's/\([^-]*-g\)/r\1/;s/-/./g' ||
printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
)
}

build() {
cmake -DCMAKE_INSTALL_PREFIX=/usr -B build -S RoundedSBE
make -C build
}

package() {
make -C build DESTDIR="${pkgdir}" PREFIX=/usr install
}
