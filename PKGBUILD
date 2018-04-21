# Script generated with Bloom
pkgdesc="ROS - rqt_rviz provides a GUI plugin embedding <a href="http://www.ros.org/wiki/rviz">RViz</a>. Note that this rqt plugin does NOT supersede RViz but depends on it."
url='http://wiki.ros.org/rqt_rviz'

pkgname='ros-lunar-rqt-rviz'
pkgver='0.5.8_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('boost'
'qt5-base'
'ros-lunar-catkin'
'ros-lunar-pluginlib'
'ros-lunar-rqt-gui'
'ros-lunar-rqt-gui-cpp'
'ros-lunar-rviz'
)

depends=('boost'
'ros-lunar-pluginlib'
'ros-lunar-rqt-gui'
'ros-lunar-rqt-gui-cpp'
'ros-lunar-rviz'
)

conflicts=()
replaces=()

_dir=rqt_rviz
source=()
md5sums=()

prepare() {
    cp -R $startdir/rqt_rviz $srcdir/rqt_rviz
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/lunar/setup.bash ] && source /opt/ros/lunar/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/lunar \
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

