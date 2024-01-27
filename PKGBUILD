# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Danilo J. S. Bellini <danilo dot bellini at gmail dot com>
# Maintainer:  Pellegrino Prevete <cGVsbGVncmlub3ByZXZldGVAZ21haWwuY29tCg== | base -d>
# Maintainer:  Truocolo <truocolo@aol.com>
# Contributor: Marcell Meszaros < marcell.meszaros AT runbox.eu >
# Contributor: Felix Yan <felixonmars@archlinux.org>
_py='python2'
_pkg="scandir"
pkgname="${_py}-${_pkg}"
_name="${_pkg}"
pkgver=1.10.0
pkgrel=8
pkgdesc='Better directory iterator and faster os.walk() alternative'
arch=(
  'x86_64'
  'arm'
  'armv7h'
  'aarch64'
  'i686'
  'pentium4'
)
url="https://github.com/benhoyt/${_pkg}"
license=(
  'BSD'
)
depends=(
  "${_py}"
)
makedepends=( 
  "${_py}-setuptools"
)
source=(
  "${pkgname}-${pkgver}.tar.gz::${url}/archive/refs/tags/v${pkgver}.tar.gz"
)
sha256sums=(
  '73a773c58432ce28f32286f2892217101f4cf61ff4bccd8829ebaa7af7c56620'
)

build() {
  cd \
    "${srcdir}/${_name}-${pkgver}"
  "${_py}" \
    setup.py \
     build
}

check() {
  cd \
    "${srcdir}/${_pkg}-${pkgver}"
  touch \
    test/__init__.py
  rm \
   -rf \
    test/testdir
  LC_ALL=C.UTF-8 \
  PYTHONPATH="$PWD/build/lib.linux-${CARCH}-2.7" \
    "${_py}" \
      -m \
        unittest \
        discover \
	  -v
}

package() {
  cd \
    "${srcdir}/${_pkg}-${pkgver}"
  "${_py}" \
    setup.py \
      install \
        --root="${pkgdir}" \
	--optimize=1 \
	--skip-build
  install \
    -Dm644 \
      LICENSE.txt \
      "$pkgdir/usr/share/licenses/$pkgname/LICENSE.txt"
}

# vim:set sw=2 sts=-1 et:
