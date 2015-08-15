# Maintainer: Simon Perry <aur [at] sanxion [dot] net>
# Contributor: Bartlomiej Piotrowski <nospam@bpiotrowski.pl>
# Contributor: Jaroslav Lichtblau <dragonlord@aur.archlinux.org>
# Contributor: Jason Pierce <`echo 'moc tod liamg ta nosaj tod ecreip' | rev`>
# Contributor: Jeremy Cowgar <jeremy@cowgar.com>
# Contributor: Simon Perry <aur [at] sanxion [dot] net>

pkgname=dropbear
pkgver=2014.65
pkgrel=1
pkgdesc="Lightweight replacement for sshd"
arch=('i686' 'x86_64' 'armv6h')
url="http://matt.ucc.asn.au/dropbear/dropbear.html"
license=('MIT')
depends=('zlib')
source=(http://matt.ucc.asn.au/$pkgname/releases/$pkgname-$pkgver.tar.bz2
        $pkgname.service)
sha256sums=('e20057aa7db0f9ea4efdcbfc6fc6b73a648b47b6ab6a01659472142b06f5f56c'
            '1920dc2d9a1dd86b3137ae4348196f9b95142d6eee484ee536bc7dfed7f0def0')

build() {
  cd ${srcdir}/$pkgname-$pkgver

  sed -i 's|usr/libexec/sftp|usr/lib/ssh/sftp|' options.h

  ./configure --prefix=/usr --bindir=/usr/bin --sbindir=/usr/bin
  make
}

package() {
  cd ${srcdir}/$pkgname-$pkgver

  DESTDIR=${pkgdir} make install

  # Configuration files
  install -d ${pkgdir}/etc/$pkgname
  install -D -m644 ${srcdir}/$pkgname.service ${pkgdir}/usr/lib/systemd/system/$pkgname.service

  # License file
  install -D -m644 LICENSE ${pkgdir}/usr/share/licenses/$pkgname/LICENSE
}

