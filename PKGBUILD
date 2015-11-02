# Contributor: VK2ACP <anthcp@gmail.com>

pkgname=allstar-using-dahdi
pkgver=0.2.0.0
pkgrel=1505
pkgdesc="Asterisk with allstar mods using dahdi"
arch=('armv6h' 'armv7h')
url="http://www.asterisk.org/"
license=('GPL2')
depends=('dahdi-allstar' 'libusb' 'perl' 'svn' 'libusb-compat' 'alsa-lib' 'wget')
makedepends=('linux-headers')
conflicts=('zaptel')
install="${pkgname}.install"
source=("svn+http://svn.ohnosec.org/svn/projects/allstar/astsrc-1.4.23-pre/#revision=${pkgrel}"
	"asterisk-allstar.service"
	"rc-updatenodelist.service"
	"rc-updatenodelist"
	"dahdi-channels.conf"
	"armv7h-update4.patch"
	"armv6h-update4.patch"
	"chan_dahdi.conf")
build() {
  patch -p0 -i "${srcdir}/${arch}-update4.patch"
  cd "${srcdir}/astsrc-1.4.23-pre/trunk"
  make makepkg-build
}
package() {
  cd "${srcdir}/astsrc-1.4.23-pre/trunk"
  make DESTDIR="${pkgdir}" install_usbradio
  mkdir -p "${pkgdir}/etc/asterisk"
  cp "${srcdir}/dahdi-channels.conf" "${pkgdir}/etc/asterisk"
  cp "${srcdir}/chan_dahdi.conf" "${pkgdir}/etc/asterisk"
  mkdir -p "${pkgdir}/usr/lib/systemd/system"
  cp "${srcdir}/asterisk-allstar.service" "${pkgdir}/usr/lib/systemd/system"
  chmod 644 "${pkgdir}/usr/lib/systemd/system/asterisk-allstar.service"
  cp "${srcdir}/rc-updatenodelist.service" "${pkgdir}/usr/lib/systemd/system"
  chmod 644 "${pkgdir}/usr/lib/systemd/system/rc-updatenodelist.service" "${pkgdir}/usr/lib/systemd/system/rc-updatenodelist.service"
  cp "$(srcdir)/rc-updatenodelist" "${pkgdir/etc/asterisk/rc-updatenodelist"
}
# vim:set ts=2 sw=2 et:
md5sums=('SKIP'
         '0f7b95440d8fe3b8a48d8fa5a1568c03'
         'SKIP'
         'SKIP'
         'cfcb5fa559c08c257ed8db8a35249d6e'
         'ce3c2f6e7797c3a699a8ba9d453de027'
         '08a18ac98ce8092f3aac48a6e2597b73'
         '05b73ea9cb98b1089b104c09150c5572')
