# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Felix Yan <felixonmars@archlinux.org>

pkgname=python-autocommand
pkgver=2.2.1
pkgrel=4
pkgdesc="A library to create a command-line program from a function"
url="https://github.com/Lucretiel/autocommand"
license=('LGPL')
arch=('any')
depends=(
  'python'
)
makedepends=(
  'python-setuptools'
  'python-jaraco.text'
)
checkdepends=('python-pytest')
source=("https://github.com/Lucretiel/autocommand/archive/$pkgver/$pkgname-$pkgver.tar.gz")
sha512sums=(
  '6ab6b7f712c9e57cefb25299e2f98359bb39fd55439fc40a5c9ed752ff54f664c9badf044418576c0dc47b1b76114d96946b2df5343b27eeb87eb24'
)

build() {
  cd autocommand-$pkgver
  python setup.py build
}

check() {
  cd autocommand-$pkgver
  PYTHONPATH="$PWD"/build/lib pytest
}

package() {
  cd autocommand-$pkgver
  python \
    setup.py \
    install \
    --root="$pkgdir" \
    --optimize=1
}

# vim:set sw=2 sts=-1 et:
