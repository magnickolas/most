# Maintainer: Stéphane Gaudreault <stephane@archlinux.org>
# Contributor: juergen <juergen@archlinux.org>
# Contributor: Tom Newsom <Jeepster@gmx.co.uk>

pkgname=most
pkgver=5.2.0
pkgrel=1
pkgdesc="A terminal pager similar to 'more' and 'less'"
arch=('x86_64')
depends=('slang')
license=('GPL')
url="https://www.jedsoft.org/most/index.html"
source=(https://www.jedsoft.org/releases/most/most-$pkgver.tar.gz{,.asc} package.patch)
validpgpkeys=('64083373E9E1DE997EBBE7784B82D0B82930237D')  # John E. Davis <davis@space.mit.edu>
sha512sums=('3aa3cb46ddd456532a009fb9cfcd746971396be33e03e52a15b754a6d7683f4efd020edb0ec4eb36d22ba20f050aaac4ba6cdd3b69bb5701ea58ddb9a903c59d'
            'SKIP'
            '260d28097bbc46d12a53b261d235641da1833860d0cb74a701ec49cb28afa3997694b482fa65c1ba4aed68028cdd6740f64aab4c60d8d5a2559297c0a08ec627')

prepare() {
  patch --directory="${pkgname}-${pkgver}" --forward --strip=1 --input="${srcdir}/package.patch"
}

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  ./configure --prefix=/usr --sysconfdir=/etc
  make
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  make DESTDIR="${pkgdir}" install
}
