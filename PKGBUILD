pkgname=osp-tracker
pkgver=4.92
arch=('x86_64')
pkgrel=1
pkgdesc='Tracker video analysis and modeling tool'
url='http://physlets.org/tracker/'
license=('GPL3')
depends=('gtk2'
         'gconf'
         'java-runtime')
source=("http://www.compadre.org/osp/images/tracker/Tracker-4.92-linux-64bit-installer.run"
        "tracker.sh"
        "tracker.desktop")
sha256sums=('0d5ba0f77990988f35039351b0aa03e8ee1d159b71531999e75c50d7b04d2837'
            'SKIP'
            'SKIP')


package() {
  echo $pkgdir
  export XDG_UTILS_INSTALL_MODE=user
  msg2 'Starting Tracker installer'
  "./Tracker-4.92-linux-64bit-installer.run" --mode text
  msg2 'Creating desktop file and symlinks'
  mkdir $pkgdir/usr $pkgdir/usr/bin
  ln -s "/opt/tracker/tracker.sh" "${pkgdir}/usr/bin/${pkgname}"
  install -D -m755 "tracker.sh" "${pkgdir}/opt/tracker/tracker.sh"
  rm -f "${pkgdir}/opt/tracker/tracker"
  ln -s "/opt/tracker" "${pkgdir}/opt/tracker/tracker"
  install -D -m644 "tracker.desktop" "${pkgdir}/usr/share/applications/${pkgname}.desktop"
  cp tracker.desktop ${pkgdir}/opt/tracker/tracker.desktop
  install -D -m644 "${pkgdir}/opt/tracker/tracker_icon48.png" "${pkgdir}/usr/share/pixmaps/${pkgname}.png"
}
