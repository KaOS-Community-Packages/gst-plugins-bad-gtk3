pkgname=libgstgtkskin
_realpkgname=gst-plugins-bad
pkgver=1.10.2
pkgrel=1
pkgdesc="A gtk plugin for Gstreamer"
arch=('x86_64')
license=('LGPL')
url="http://gstreamer.freedesktop.org/"
depends=( 'gst-plugins-base' 'gtk3')
makedepends=('gobject-introspection')
options=('!libtool' '!emptydirs')
source=("http://gstreamer.freedesktop.org/src/gst-plugins-bad/${_realpkgname}-${pkgver}.tar.xz")
md5sums=('823f4c33fe27c61332c0122273217988')

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

