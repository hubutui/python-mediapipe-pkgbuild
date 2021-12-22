# Maintainer: Butui Hu <hot123tea123@gmail.com>

pkgname=python-mediapipe
pkgver=0.8.9.1
pkgrel=1
pkgdesc='Cross-platform, customizable ML solutions for live and streaming media'
arch=('x86_64')
url='https://mediapipe.dev'
license=('Apache')
depends=(
  absl-py
  ffmpeg
  openexr
  python-attrs
  python-matplotlib
  python-numpy
  python-opencv
  python-protobuf
)
makedepends=(
  python-pip
)
source=("https://files.pythonhosted.org/packages/49/60/a1619ba4edd89fa78a687c0fb94476bb55a2e37e8d380bbd756b8a7934fd/mediapipe-${pkgver}-cp310-cp310-manylinux_2_17_x86_64.manylinux2014_x86_64.whl")
sha256sums=('2cb270484071c7a8469b8107727a42696932fa9d8b8e9dcfe04ab8268bdc4bef')

package() {
  PIP_CONFIG_FILE=/dev/null pip install --isolated --root="${pkgdir}" --ignore-installed --no-deps "${srcdir}/"*.whl
  python -O -m compileall "${pkgdir}"
}
