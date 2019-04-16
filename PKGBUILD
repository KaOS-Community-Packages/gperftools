pkgname=gperftools
pkgver=2.7
pkgrel=1
pkgdesc="Fast, multi-threaded malloc and nifty performance analysis tools"
arch=('x86_64')
url="https://github.com/gperftools/gperftools"
license=('BSD')
depends=('perl')
provides=('libtcmalloc.so'
          'libprofiler.so'
          'libtcmalloc_debug.so'
          'libtcmalloc_and_profiler.so'
          'libtcmalloc_minimal.so'
          'libtcmalloc_minimal_debug.so')
makedepends=('git')
optdepends=('graphviz: pprof graph generation'
            'gv: pprof postscript generation')
source=("git+https://github.com/gperftools/gperftools#tag=$pkgname-$pkgver")
md5sums=('SKIP')

prepare() {
  cd "$pkgname"

  ./autogen.sh
}

build() {
  cd "$pkgname"

  ./configure --prefix=/usr --enable-frame-pointers
  make
}

package() {
  cd "$pkgname"

  make DESTDIR="$pkgdir" install
  install -Dm644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
}
