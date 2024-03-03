_rga_commit=d7a0a485ed6c201f882c20b3a8881e801f131385
pkgname=librga-multi
pkgver="1.10.0.${_rga_commit:0:10}"
pkgrel=1
pkgdesc='Rockchip RGA User-Space Library'
arch=('aarch64' 'armv7h')
url='https://github.com/JeffyCN/mirrors/tree/linux-rga-multi'
license=('Apache')
depends=('gcc-libs' 'meson')
makedepends=('meson')
source=("${pkgname}-${pkgver}".tar.gz::"https://github.com/JeffyCN/mirrors/archive/${_rga_commit}.tar.gz"
        "normalrga-cpp-add-10b-compact-endian-mode.patch")
sha256sums=('SKIP'
            '26f2990818d6b6412c7f1d57b27cacc3d3e30b7ffad1fd678b5d2d991f1f4c74')
options=(!lto strip)

prepare() {
  cd mirrors-*
  patch -Np1 -i ../normalrga-cpp-add-10b-compact-endian-mode.patch
}

build() {
  cd mirrors-*
  meson setup --reconfigure builddir --prefix="$pkgdir/usr"
  ninja ${MAKEFLAGS} -C builddir
}

package() {
  provides=($pkgname)
  onflicts=($pkgname rga librga)
  cd mirrors-*
  ninja ${MAKEFLAGS} -C builddir install
}