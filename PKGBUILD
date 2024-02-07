# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Maintainer:  Pellegrino Prevete <cGVsbGVncmlub3ByZXZldGVAZ21haWwuY29tCg== | base -d>
# Maintainer:  Truocolo <truocolo@aol.com>

pkgname=python-autocommand
pkgver=2.2.1
pkgrel=4
pkgdesc="A library to create a command-line program from a function"
url="https://github.com/Lucretiel/autocommand"
license=(
  'LGPL'
)
arch=('any')
depends=(
  'python'
)
makedepends=(
  'python-setuptools'
  'python-jaraco.text'
)
checkdepends=('python-pytest')
source=(
  "${url}/archive/$pkgver/$pkgname-$pkgver.tar.gz"
)
sha256sums=(
  '0c320f9dd256ad133dcfb6476ff95a36727351930122cc14d3e91810ec1f09cd'
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
