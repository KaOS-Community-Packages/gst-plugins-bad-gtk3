pkgname=libgstgtkskin
_realpkgname=gst-plugins-bad
pkgver=1.10.3
pkgrel=1
pkgdesc="A gtk plugin for Gstreamer"
arch=('x86_64')
license=('LGPL')
url="http://gstreamer.freedesktop.org/"
depends=( 'gst-plugins-base' 'gtk3')
makedepends=('gobject-introspection')
options=('!libtool' '!emptydirs')
source=("http://gstreamer.freedesktop.org/src/gst-plugins-bad/${_realpkgname}-${pkgver}.tar.xz")
md5sums=('e59798c86a670041de2e61856ea43d2a')

build() {
  cd ${_realpkgname}-${pkgver}
  
  CXXFLAGS="-std=c++11"
  
  ./configure --prefix=/usr \
    --sysconfdir=/etc \
    --localstatedir=/var \
    --disable-static \
    --with-package-name="GStreamer (KaOS)" \
    --with-package-origin="http://kaosx.us"
    
  sed -i -e 's/ -shared / -Wl,-O1,--as-needed\0/g' libtool 
  
  make 
}


package() {
  cd ${_realpkgname}-${pkgver}
  
  make -C ext/gtk DESTDIR="${pkgdir}" install 

}

