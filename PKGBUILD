# Maintainer: György Balló <ballogy@freestart.hu>
pkgname=ubuntuone-client-gnome
pkgver=2.99.3
pkgrel=1
pkgdesc="Some plug-ins, extensions, and data for integrating Ubuntu One features in some core parts of GNOME"
arch=('i686' 'x86_64')
url="https://launchpad.net/ubuntuone-client-gnome"
license=('GPL')
depends=('nautilus' 'evolution-data-server' 'ubuntuone-client' 'gnome-settings-daemon')
makedepends=('intltool')
options=(!libtool)
install=$pkgname.install
source=(http://launchpad.net/ubuntuone-client-gnome/stable-3-0/$pkgver/+download/$pkgname-$pkgver.tar.gz
        launchpad-export.tar.gz)
md5sums=('4365daf9683d952eaa3a25a0039799f4'
         '0be157a1e7ba1907845e0ffa703a64e6')

build() {
  cd "$srcdir/$pkgname-$pkgver"
  echo 'am ar ast be bn bs ca ca@valencia cs da de el en_AU en_GB eo es et eu fi fr gl he hr hu id it ja kk ko lt lv ms nb nl oc pl pt pt_BR ro ru sk sl sq sr sv te th tr ug uk vi zh_CN zh_HK zh_TW' >po/LINGUAS
  rename $pkgname- '' ../po/$pkgname-*.po
  mv -f -t po ../po/*

  ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var \
              --disable-static --disable-schemas-compile
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"

  make DESTDIR="$pkgdir/" install
}
