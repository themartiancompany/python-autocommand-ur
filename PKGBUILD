# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Felix Yan <felixonmars@archlinux.org>

_build="true"
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
pkgrel=1
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
if [[ "${_build}" == "true" ]]; then
  makedepends+=(
    "${_py}-build"
    "${_py}-installer"
  )
fi
checkdepends=(
  "${_py}-pytest"
)
_jaraco_commit="ec6f6641"
source=(
  "${url}/archive/${pkgver}/${pkgname}-${pkgver}.tar.gz"
  "${_http}/jaraco/${_pkg}/commit/ec6f6641.patch"
)
sha512sums=(
  '5ed109db16a0e309ed5107b26db0b70ed8669d73817e82eb5a219650d29f53785aa1f9471b2ac71d21dbffc9f0a13ea0fdf69e63ab534fd84407a1d6741cf5b5'
  '2a31e24bafeab219b9ba836c34efa08664ddc323592cbff6cf7853631c982ebac2f263077999cd8c7aa05a2e588f64c8a1bcc4819436b8aba7068b1a26f21019'
)

prepare() {
  cd \
    "${_pkg}-${pkgver}"
  # Fix build
  patch \
    -p1 \
    -i ../"${_jaraco_commit}.patch"
}

build() {
  cd \
    "${_pkg}-${pkgver}"
  if [[ "${_build}" == "true" ]]; then
  "${_py}" \
    -m build \
    -wn
  elif [[ "${_build}" == "false" ]]; then
  "${_py}" \
    setup.py \
      build
  fi
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
  if [[ "${_build}" == "false" ]]; then
  "${_py}" \
    setup.py \
    install \
    --root="${pkgdir}" \
    --optimize=1
  elif [[ "${_build}" == "true" ]]; then
    "${_py}" \
      -m \
        installer \
      --destdir="${pkgdir}" \
      dist/*.whl
  fi
}

# vim:set sw=2 sts=-1 et:
