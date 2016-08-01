pkgname=gst-plugins-bad-gtk3
_realpkgname=gst-plugins-bad
pkgver=1.8.2
pkgrel=1
pkgdesc="GStreamer Multimedia Framework Bad Plugins, built with gtk3 support"
arch=('x86_64')
license=('LGPL')
url="http://gstreamer.freedesktop.org/"
depends=('mjpegtools' 'gst-plugins-base' 'curl' 'chromaprint' 'libmms' 'faad2'
         'mpg123' 'faac' 'celt' 'libdca' 'soundtouch' 'libdvdnav' 'gtk3'
         'libmodplug' 'libgme' 'opus' 'wayland' 'neon' 'libofa' 'fluidsynth' 'openjpeg'
         'libwebp' 'libsrtp' 'gnutls' 'librsvg' 'libpng' 'libgudev' 'sbc' 'glu'
         'qt5-x11extras')
makedepends=('schroedinger' 'libexif' 'libdvdread' 'libvdpau' 'libmpeg2' 'python3' 
             'gobject-introspection' 'bluez' 'ladspa' 'openal' 'qt5-wayland')
options=('!libtool' '!emptydirs')
conflicts=('gst-plugins-bad')
provides=('gst-plugins-bad')
source=("http://gstreamer.freedesktop.org/src/gst-plugins-bad/${_realpkgname}-${pkgver}.tar.xz")
md5sums=('83abc2e70684e7b195f18ca2992ef6e8')

build() {
  cd ${_realpkgname}-${pkgver}
  
  CXXFLAGS="-std=c++11"
  
  ./configure --prefix=/usr \
    --sysconfdir=/etc \
    --localstatedir=/var \
    --disable-static \
    --enable-experimental \
    --with-package-name="GStreamer (KaOS)" \
    --with-package-origin="http://kaosx.us"
    
  sed -i -e 's/ -shared / -Wl,-O1,--as-needed\0/g' libtool 
  
  make
}

check() {
  cd ${_realpkgname}-${pkgver}
  
  make -k check || :
}

package() {
  cd ${_realpkgname}-${pkgver}
  
  make DESTDIR="${pkgdir}" install
}
