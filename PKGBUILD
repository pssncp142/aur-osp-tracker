pkgname=osp-tracker
pkgver=4.94
arch=('x86_64')
pkgrel=1
pkgdesc='Tracker video analysis and modeling tool'
url='http://physlets.org/tracker/'
license=('GPL3')
depends=('gtk2'
         'gconf'
         'java-runtime')
_runname="Tracker-${pkgver}-linux-64bit-installer.run"
source=("http://www.compadre.org/osp/images/tracker/${_runname}"
        "tracker.sh"
        "tracker.desktop")
sha256sums=('55af3e01effb04d7149ee9c9191c762aeb9a96e8d2dbcb013af3ee9953753174'
            'SKIP'
            'SKIP')

package() {
  echo "${pkgdir}"
  export XDG_UTILS_INSTALL_MODE=user
  msg2 'Starting Tracker installer'
  chmod +x "./${_runname}"
  "./${_runname}" \
	  --mode text \
	  --tracker-home "${pkgdir}/opt/tracker" \
	  --experiments-home "${pkgdir}/opt/tracker/share" \
	  --unattendedmodeui minimal \
	  --enable-components Experiments
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
