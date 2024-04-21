# Maintainer: Antonio Rojas <arojas@archlinux.org>
# Contributor: Elmar Klausmeier <Elmar.Klausmeier@gmail.com>
# Contributor: Chris Gorman <chrisjohgorman@gmail.com>

pkgname=sundials64
_pkgname=sundials
pkgver=7.0.0
pkgrel=1
pkgdesc='Suite of nonlinear differential/algebraic equation solvers'
arch=(x86_64)
url='https://computing.llnl.gov/projects/sundials'
license=(BSD)
depends=(openmpi
         suitesparse64)
makedepends=(cmake
             gcc-fortran
             python)
conflicts=(sundials)
provides=(sundials)
source=(https://github.com/LLNL/sundials/archive/v$pkgver/$_pkgname-$pkgver.tar.gz)
sha256sums=('63d1f76207161612f36f5017d8333e00e5297b0cd8cbc4628f5dd54102c763a6')

build() {
  cmake -B build -S $_pkgname-$pkgver \
    -DSUNDIALS_INDEX_SIZE=64 \
    -DCOLAMD_DIR=/usr/lib/cmake/COLAMD64 \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DBUILD_STATIC_LIBS=OFF \
    -DENABLE_MPI=ON \
    -DENABLE_PTHREAD=ON	\
    -DENABLE_OPENMP=ON \
    -DENABLE_KLU=ON \
    -DKLU_LIBRARY_DIR=/usr/lib \
    -DKLU_INCLUDE_DIR=/usr/include/suitesparse64 \
    -DEXAMPLES_INSTALL_PATH=/usr/share/sundials/examples
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build

  install -Dm644 $_pkgname-$pkgver/LICENSE -t "$pkgdir"/usr/share/licenses/$pkgname
}
