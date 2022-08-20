pkgname=qt5-notifyd
pkgver=1.0
pkgrel=1
pkgdesc="Notification daemon"
arch=("x86_64")
license=("GPL3")
makedepends=("cmake")
depends=("qt5-base")

source=("git+https://github.com/git-fal7/$pkgname")
sha256sums=("SKIP")

build() {
	mkdir -p ../build
	cd ../build
	cmake "$srcdir/$pkgname" -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_INSTALL_LIBDIR=lib
	make
}


package() {
	cd ../build
	make DESTDIR="$pkgdir" install
}
