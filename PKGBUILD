pkgver=1.9.3.1
pkgname=librga-multi
pkgrel=1
pkgdesc='Rockchip RGA User-Space Library'
arch=('aarch64' 'armv7h')
url='https://github.com/airockchip/librga'
_url_pkg='https://github.com/7Ji-PKGBUILDs/librga-multi'
_url_mirror='https://github.com/JeffyCN/mirrors/tree/linux-rga-multi'
license=('Apache')
depends=('gcc-libs' 'meson')
makedepends=('meson')
source=("${_url_pkg}/releases/download/assets/${pkgname}-v${pkgver}.tar.gz"
        "normalrga-cpp-add-10b-compact-endian-mode.patch")
sha256sums=('1cbe37b5d67447aca73d72e66c17ca8342aa47daf74deefa0e5649d21b1c802c'
            '26f2990818d6b6412c7f1d57b27cacc3d3e30b7ffad1fd678b5d2d991f1f4c74')
options=(!lto)

prepare() {
    cd $pkgname
    patch -Np1 -i ../normalrga-cpp-add-10b-compact-endian-mode.patch
}

build() {
    arch-meson --reconfigure build $pkgname
    meson compile -C build
}

package() {
    provides=($pkgname)
    conflicts=($pkgname rga librga)
    meson install -C build --destdir $pkgdir
}