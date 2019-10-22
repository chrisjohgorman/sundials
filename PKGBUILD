# Maintainer: Antonio Rojas <arojas@archlinux.org>
# Contributor: Elmar Klausmeier <Elmar.Klausmeier@gmail.com>

pkgname=sundials
pkgver=5.0.0
pkgrel=1
pkgdesc="Suite of nonlinear differential/algebraic equation solvers"
arch=(x86_64)
url="https://computation.llnl.gov/casc/sundials/main.html"
license=(BSD)
depends=(openmpi suitesparse)
makedepends=(cmake gcc-fortran python)
source=("https://computation.llnl.gov/projects/sundials/download/$pkgname-$pkgver.tar.gz")
sha256sums=('345141ec01c641d0bdfb3476c478b7e74fd6a7192a478a27cafe75d9da2d7dd3')

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../$pkgname-$pkgver \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DMPI_ENABLE=ON \
    -DPTHREAD_ENABLE=ON	\
    -DOPENMP_ENABLE=ON \
    -DF77_INTERFACE_ENABLE=ON \
    -DKLU_ENABLE=ON \
    -DKLU_LIBRARY_DIR=/usr/lib \
    -DEXAMPLES_INSTALL_PATH=/usr/share/sundials/examples
  make
}

package() {
  cd build
  make DESTDIR="$pkgdir" install

  install -Dm644 "$srcdir"/$pkgname-$pkgver/LICENSE -t "$pkgdir"/usr/share/licenses/$pkgname
}
