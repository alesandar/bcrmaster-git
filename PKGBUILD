# Maintainer: alesandar <publicvoid at tuta dot io>

pkgname=bcrmaster-git
pkgver=1.0.4.r1.9d730c7
pkgrel=1
pkgdesc="GUI application for Behringer BCR 2000, written in BCL"
arch=('x86_64')
url="https://github.com/christofmuc/BCR2000_Master"
license=('GPL')
groups=()
depends=('alsa-lib' 'gtk3' 'webkit2gtk' 'glew' 'boost-libs')
makedepends=('git' 'curl' 'pkgconfig')
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
replaces=()
backup=()
options=()
install=
source=("${pkgname%-git}::git+https://github.com/christofmuc/BCR2000_Master#branch=master")
noextract=()
md5sums=('SKIP')

pkgver() {
  cd "${srcdir}/${pkgname%-git}"
  printf "%s" "$(git describe --long | sed 's/\([^-]*-\)g/r\1/;s/-/./g')"
}

prepare() {
  cd "${srcdir}/${pkgname%-git}"
  git submodule update --recursive --init --depth 1
}

build() {
  cd "${srcdir}/${pkgname%-git}"
  cmake -S . -B build -DCMAKE_BUILD_TYPE='None' -Wno-dev
  cmake --build build
}

package() {
  cd "${srcdir}/${pkgname%-git}"
  cmake --install build
  install -D -m755 build/BCRMaster/BCRMaster "${pkgdir}/usr/bin/BCRMaster"
}
