# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Felix Yan <felixonmars@archlinux.org>

_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pkg=autocommand
pkgname="${_py}-${_pkg}"
pkgver=2.2.2
pkgrel=4
pkgdesc="A library to create a command-line program from a function"
_http="https://github.com"
_ns="Lucretiel"
url="${_http}/${_ns}/${_pkg}"
license=(
  'LGPL'
)
arch=(
  'any'
)
depends=(
  "${_py}>=${_pymajver}"
)
makedepends=(
  "${_py}-setuptools"
)
checkdepends=(
  "${_py}-pytest"
)
source=(
  "${url}/archive/${pkgver}/${pkgname}-${pkgver}.tar.gz"
)
sha512sums=(
  '5ed109db16a0e309ed5107b26db0b70ed8669d73817e82eb5a219650d29f53785aa1f9471b2ac71d21dbffc9f0a13ea0fdf69e63ab534fd84407a1d6741cf5b5'
)

build() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    setup.py \
      build
}

check() {
  cd \
    "${_pkg}-${pkgver}"
  PYTHONPATH="$PWD"/build/lib \
  pytest
}

package() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    setup.py \
    install \
    --root="${pkgdir}" \
    --optimize=1
}

# vim:set sw=2 sts=-1 et:
