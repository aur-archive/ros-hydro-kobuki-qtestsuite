# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - An rqt plugin that provides a graphical, interactive testsuite for Kobuki."
url='http://ros.org/wiki/kobuki_qtestsuite'

pkgname='ros-hydro-kobuki-qtestsuite'
pkgver='0.3.2'
_pkgver_patch=1
arch=('any')
pkgrel=3
license=('BSD')

ros_makedepends=(ros-hydro-rqt-gui-py
  ros-hydro-kobuki-testsuite
  ros-hydro-rospy
  ros-hydro-qt-gui-py-common
  ros-hydro-rqt-gui
  ros-hydro-geometry-msgs
  ros-hydro-catkin
  ros-hydro-rqt-py-common
  ros-hydro-nav-msgs
  ros-hydro-rqt-plot)
makedepends=('cmake' 'git' 'ros-build-tools'
  ${ros_makedepends[@]}
  python2-pyqt4-10)

ros_depends=(ros-hydro-rqt-gui-py
  ros-hydro-kobuki-testsuite
  ros-hydro-rospy
  ros-hydro-qt-gui-py-common
  ros-hydro-rqt-gui
  ros-hydro-geometry-msgs
  ros-hydro-rqt-py-common
  ros-hydro-nav-msgs
  ros-hydro-rqt-plot)
depends=(${ros_depends[@]}
  python2-pyqt4-10)

_tag=release/hydro/kobuki_qtestsuite/${pkgver}-${_pkgver_patch}
_dir=kobuki_qtestsuite
source=("${_dir}"::"git+https://github.com/yujinrobot-release/kobuki_desktop-release.git"#tag=${_tag})
md5sums=('SKIP')

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/hydro/setup.bash ] && source /opt/ros/hydro/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/hydro \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
