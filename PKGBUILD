# Contributor: VK2ACP <anthcp@gmail.com>
# Supplemental contributions: K2DLS <k2dls@arrl.net>

pkgname=allstar-using-dahdi
pkgver=0.2.0.1
pkgrel=1505
pkgdesc="Asterisk with allstar mods using dahdi"
arch=('armv6h' 'armv7h')
url="http://www.asterisk.org/"
license=('GPL2')
depends=('dahdi-allstar' 'libusb' 'perl' 'svn' 'libusb-compat' 'alsa-lib' 'wget' 'rsync')
makedepends=('linux-headers')
conflicts=('zaptel')
install="${pkgname}.install"
source=("svn+http://svn.ohnosec.org/svn/projects/allstar/astsrc-1.4.23-pre/#revision=${pkgrel}"
	"asterisk-allstar.service"
	"rc-updatenodelist.service"
	"dahdi-channels.conf"
	"armv7h-update4.patch"
	"armv6h-update4.patch"
	"chan_dahdi.conf")
backup=("etc/asterisk/extensions.conf"
	"etc/asterisk/iax.conf"
	"etc/asterisk/rpt.conf"
	"etc/asterisk/sip.conf"
	"etc/asterisk/usbradio.conf"
	"etc/asterisk/rc.updatenodelist")
build() {
  patch -p0 -i "${srcdir}/${arch}-update4.patch"
  cd "${srcdir}/astsrc-1.4.23-pre/trunk"
  make makepkg-build
}
package() {
  cd "${srcdir}/astsrc-1.4.23-pre/trunk"
  mkdir -p -m 750 "${pkgdir}/etc/asterisk"
  make DESTDIR="${pkgdir}" install_usbradio
  cp "${srcdir}/dahdi-channels.conf" "${pkgdir}/etc/asterisk"
  cp "${srcdir}/chan_dahdi.conf" "${pkgdir}/etc/asterisk"
  mkdir -p "${pkgdir}/usr/lib/systemd/system"
  cp "${srcdir}/asterisk-allstar.service" "${pkgdir}/usr/lib/systemd/system"
  cp "${srcdir}/rc-updatenodelist.service" "${pkgdir}/usr/lib/systemd/system"
  cp "${srcdir}/astsrc-1.4.23-pre/trunk/allstar/rc.updatenodelist" \
     "${pkgdir}/etc/asterisk"
  chown -R root:root "${pkgdir}/etc/asterisk"
  chown -R root:root "${pkgdir}/var/lib/asterisk/sounds/rpt/nodenames"
}
md5sums=('SKIP'
	 '78f6defed7cffd8ffb7c62fd746d7171'
	 '0b9763eeb32e15df201bea388eb516b4'
	 'cfcb5fa559c08c257ed8db8a35249d6e'
	 'ce3c2f6e7797c3a699a8ba9d453de027'
	 '08a18ac98ce8092f3aac48a6e2597b73'
	 '05b73ea9cb98b1089b104c09150c5572')
# vim:set ts=2 sw=2 et:
