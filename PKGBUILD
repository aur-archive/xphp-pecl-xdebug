# Maintainer: Andrew Rose <hello@andrewrose.co.uk>
# Contributor: Andrew Rose <hello@andrewrose.co.uk>

pkgname=xphp-pecl-xdebug
pkgdesc='Provides functions for function traces and profiling'
pkgver=2.2.6
pkgrel=1

arch=('x86_64' 'i686')
license=('PHP')
url='http://pecl.php.net/package/xdebug'

makedepends=('xphp')
source=("http://pecl.php.net/get/xdebug-${pkgver}.tgz")
md5sums=('f216356861e27284580d0208060ea7fa')
depends=('xphp')

peclconfig="--prefix=/opt/xphp \
 --bindir=/opt/xphp/bin \
 --libdir=/opt/xphp/lib \
 --sysconfdir=/etc/xphp \
 --mandir=/opt/xphp/man \
 --with-php-config=/opt/xphp/bin/php-config
"

build() {
	export PATH="/opt/xphp/bin:$PATH"

 	cd ${srcdir}/xdebug-${pkgver} || return 1
 	/opt/xphp/bin/phpize || return 1
	./configure ${peclconfig} || return 1
	make || return 1
}

package_xphp-pecl-xdebug() {

	install -d -m755 ${pkgdir}/opt/xphp/lib/modules/
	cp ${srcdir}/xdebug-${pkgver}/modules/xdebug.so ${pkgdir}/opt/xphp/lib/modules/xdebug.so
	install -D -m 644 $startdir/xdebug.ini ${pkgdir}/etc/xphp/conf.d/xdebug.ini || return 1
}
