#Maintainer: Tor Arne Thune <http://devia.org/contact>
#Contributor: Jelle van der Waa <jelle@vdwaa.nl>

pkgname=python2-dateutil1
pkgver=2.1
pkgrel=8
pkgdesc="Provides powerful extensions to the standard datetime module"
arch=('any')
license=('custom:PYTHON')
url="http://labix.org/python-dateutil"
makedepends=('python2-setuptools' 'python2-six')
provides=('python2-dateutil=2.1')
conflicts=('python2-dateutil')
source=(http://pypi.python.org/packages/source/p/python-dateutil/python-dateutil-$pkgver.tar.gz{,.asc} python-dateutil-2.1-open-utf-8.patch)
md5sums=('1534bb15cf311f07afaa3aacba1c028b' '4aa0ba908299d983781c58ec0640ef2b' '4b780c62fc03be161629ee08e35eba6a')
validpgpkeys=('772C80C2B62C51FA8A5C952778244A9E30051117')

build() {
  cd $srcdir/python-dateutil-$pkgver
  patch -Np0 -i $srcdir/python-dateutil-2.1-open-utf-8.patch
}

package() {
depends=('python2' 'python2-six')
  cd $srcdir/python-dateutil-$pkgver
  python2 setup.py install --root=$pkgdir --optimize=1
  install -Dm644 LICENSE $pkgdir/usr/share/licenses/$pkgname/LICENSE

  chmod -R a+r $pkgdir/usr/lib/python2.7/
  rm $pkgdir/usr/lib/python2.7/site-packages/dateutil/zoneinfo/zoneinfo--latest.tar.gz
}

check() {
  cd $srcdir/python-dateutil-$pkgver
  python2 test.py
}
