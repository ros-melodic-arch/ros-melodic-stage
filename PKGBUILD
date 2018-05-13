# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - Mobile robot simulator http://rtv.github.com/Stage."
url='http://rtv.github.com/Stage'

pkgname='ros-melodic-stage'
pkgver='4.3.0'
_pkgver_patch=0
arch=('any')
pkgrel=1
license=('GPL')

ros_makedepends=()
makedepends=('cmake' 'ros-build-tools'
  ${ros_makedepends[@]}
  fltk
  libjpeg-turbo
  gtk2
  libtool
  mesa
  pkg-config)

ros_depends=(ros-melodic-catkin)
depends=(${ros_depends[@]}
  libjpeg-turbo
  mesa
  fltk
  gtk2)

# Git version (e.g. for debugging)
# _tag=release/melodic/stage/${pkgver}-${_pkgver_patch}
# _dir=${pkgname}
# source=("${_dir}"::"git+https://github.com/ros-gbp/stage-release.git"#tag=${_tag})
# sha256sums=('SKIP')

# Tarball version (faster download)
_dir="stage-release-release-melodic-stage-${pkgver}-${_pkgver_patch}"
source=("${pkgname}-${pkgver}-${_pkgver_patch}.tar.gz"::"https://github.com/ros-gbp/stage-release/archive/release/melodic/stage/${pkgver}-${_pkgver_patch}.tar.gz")
sha256sums=('3c72bba7242ecd98b26f177e4227aef06ec85915f196ee88ec6103be4dfb492d')

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/melodic/setup.bash ] && source /opt/ros/melodic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/melodic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
