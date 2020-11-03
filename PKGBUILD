# Maintainer: Antonio Rojas <arojas@archlinux.org>
# Contributor: Elmar Klausmeier <Elmar.Klausmeier@gmail.com>

pkgname=sundials
pkgver=5.5.0
pkgrel=1
pkgdesc="Suite of nonlinear differential/algebraic equation solvers"
arch=(x86_64)
url="https://computation.llnl.gov/casc/sundials/main.html"
license=(BSD)
depends=(openmpi suitesparse)
makedepends=(cmake gcc-fortran python)
source=("https://computation.llnl.gov/projects/sundials/download/$pkgname-$pkgver.tar.gz")
sha256sums=('2a755e89aab96d2ff096a4e30bf00bb162e80be20e9e99f424dccfb249098237')

build() {
  cmake -B build -S $pkgname-$pkgver \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_C_FLAGS="${CFLAGS} -fPIC -fcommon" \
    -DMPI_ENABLE=ON \
    -DPTHREAD_ENABLE=ON	\
    -DOPENMP_ENABLE=ON \
    -DF77_INTERFACE_ENABLE=ON \
    -DKLU_ENABLE=ON \
    -DKLU_LIBRARY_DIR=/usr/lib \
    -DEXAMPLES_INSTALL_PATH=/usr/share/sundials/examples
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build

  install -Dm644 $pkgname-$pkgver/LICENSE -t "$pkgdir"/usr/share/licenses/$pkgname
}
