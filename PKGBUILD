# Maintainer: Alastair Pharo <asppsa at gmail dot com>
# Contributor: Felix Morgner <felix.morgner@gmail.com>
# Contributor: Vlad M. <vlad@archlinux.net>
# Contributor: Mario Rodas
# Contributor: Oozyslug <oozyslug at gmail dot com>
# Contributor: koral <koral at mailoo dot org>
# Contributor: Anders Bennehag

pkgname=nix
pkgver=2.3.1
pkgrel=1
pkgdesc="A purely functional package manager"
arch=('i686' 'x86_64' 'armv7h')
url="https://nixos.org/nix"
license=('LGPL')
depends=('gc' 'libsodium' 'boost' 'brotli' 'editline')
optdepends=('archlinux-nix: tools to help with setup of Nix')
makedepends=('bzip2' 'openssl')
install=nix.install
source=("https://nixos.org/releases/nix/nix-$pkgver/nix-$pkgver.tar.xz")
sha256sums=('bb6578e9f20eebab6d78469ecc59c450ac54f276e5a86a882015d98fecb1bc7b')

prepare() {
  cd "$pkgname-$pkgver"
}

build () {
  cd "$pkgname-$pkgver"
  ./configure --prefix=/usr \
              --libexecdir="/usr/lib/$pkgname" \
              --sysconfdir=/etc \
              --enable-gc
  make
}

package() {
  cd "$pkgname-$pkgver"
  make DESTDIR="$pkgdir" install
  install -Dm644 COPYING "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
