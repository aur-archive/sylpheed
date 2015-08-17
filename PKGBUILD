# Maintainer: SpepS <dreamspepser at yahoo dot it>
# Contributor: Alexander Fehr <pizzapunk gmail com>
# Contributor: dorphell <dorphell@archlinux.org>

pkgname=sylpheed
pkgver=3.1.4
pkgrel=1
pkgdesc="Lightweight and user-friendly e-mail client"
arch=('i686' 'x86_64')
url="http://sylpheed.sraoss.jp/en/"
license=('GPL')
depends=('gpgme' 'gtkspell')
makedepends=('compface' 'openssl')
options=('!libtool')
install="$pkgname.install"
source=("http://sylpheed.sraoss.jp/$pkgname/v3.1/$pkgname-$pkgver.tar.bz2")
md5sums=('4e0e41f05607e5c2542a7dfd166aee77')

build() {
  cd "$srcdir/$pkgname-$pkgver"

  # glib2 fix
  sed -i '/glibconfig/d' libsylph/defs.h

  ./configure --prefix=/usr \
              --enable-ldap
  make

  # Build Attachment-Tool Plug-in
  cd plugin/attachment_tool && make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"

  make DESTDIR="$pkgdir/" install

  # Install Attachment-Tool Plug-in
  cd plugin/attachment_tool && make DESTDIR="$pkgdir/" install-plugin
}
