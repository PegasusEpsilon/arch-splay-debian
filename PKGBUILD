# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

# Maintainer: The Almighty Pegasus Epsilon <pegasus@pimpninjas.org>
pkgname=splay
pkgver=0.9.5.2_debian14
pkgrel=1
pkgdesc="Splay: An alternative mp3 player"
url="https://packages.debian.org/source/sid/splay"
arch=('i686' 'x86_64')
license=('GPL')
depends=()
provides=('splay')
conflicts=()
replaces=()

prepare() {
	wget http://http.debian.net/debian/pool/main/s/splay/splay_0.9.5.2.orig.tar.gz
	wget http://http.debian.net/debian/pool/main/s/splay/splay_0.9.5.2-14.debian.tar.xz
	tar -zxvf splay_0.9.5.2.orig.tar.gz
	tar -Jxvf splay_0.9.5.2-14.debian.tar.xz
	mv splay-0.9.5.2/* .
	rmdir splay-0.9.5.2
	for i in $(cat debian/patches/series); do
		patch -p1 < debian/patches/$i
	done
}

build() {
	aclocal
	automake --add-missing
	./configure --prefix=/usr
	make
}

package() {
	make DESTDIR="$pkgdir/" install
}
