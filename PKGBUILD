# Maintainer: Yangtse <yangtsesu@gmail.com> 
# Contributor: WU Jun <quark at lihdd dot net>

pkgname=libpinyin
pkgver=0.7.92
pkgrel=1
pkgdesc="Library to deal with pinyin."
arch=('i686' 'x86_64')
url="https://github.com/libpinyin/libpinyin"
license=('GPL')
depends=('db' 'glib2')
options=(!libtool)
source=("https://github.com/downloads/libpinyin/libpinyin/${pkgname}-lite-${pkgver}.tar.gz"
	'https://github.com/downloads/libpinyin/libpinyin/model.text.tar.gz')
noextract=("model.text.tar.gz")

md5sums=('697778a2164f0176add124788b1c85bb'
	 '59be0e37b0834e41be9786d3b2fcc129')

build() {
  cd ${srcdir}/${pkgname}-${pkgver}
  cp "${srcdir}/model.text.tar.gz" "${srcdir}/${pkgname}-${pkgver}/data/"
  sed -i '/wget.*model\.text\.tar\.gz/ d' ${srcdir}/${pkgname}-${pkgver}/data/Makefile.am

  aclocal && libtoolize --force && autoheader && automake -a && autoconf
  ./configure --prefix=/usr && make
}

package() {
  cd ${srcdir}/libpinyin-$pkgver
  make DESTDIR=${pkgdir} install
}
