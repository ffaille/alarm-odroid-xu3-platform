# ODROID-XU3/XU4/HC1/HC2/MC1 platform files and tweaks
# Maintainer: Kevin Mihelich <kevin@archlinuxarm.org>

buildarch=4

pkgname=odroid-xu3-platform
pkgver=24.03
pkgrel=1
pkgdesc="ODROID-XU3/XU4/HC1/HC2/MC1 platform files and tweaks"
arch=('armv7h')
url='https://github.com/mdrjr/5422_platform'
_commit=18feddd27e725f9ffd9223325a0a6a971e500457
license=('GPL')
makedepends=('git')
install=$pkgname.install
source=("$pkgname::git+https://github.com/mdrjr/5422_platform.git#commit=$_commit"
        '0001-odroid-tweaks-plus.patch'
        '0002-odroid-tweaks-add-arg-on-service.patch'
        '0003-postinstall-pak-to-udev-usb_modeswitch-rules.patch'
        'odroid-xu3.hook')
md5sums=('SKIP'
         '4a187e5e1446eb0c5793e2f0f05a8f2e'
         '2657df5b0a5953d10b8eb01090b0c41c'
         '35e7ca13dfb4402c296752e38cca8068'
         '485a1865fb0aaf4606cb64c379681cd0')

prepare() {
  cd $pkgname

  patch -p1 -i ../0001-odroid-tweaks-plus.patch
  sed -i 's/arm-linux-gnueabihf\///g' odroid-tweaks
  patch -p1 -i ../0002-odroid-tweaks-add-arg-on-service.patch
  patch -p1 -i ../0003-postinstall-pak-to-udev-usb_modeswitch-rules.patch -o 40-usb_modeswitch.rules
  mv ../odroid-xu3.hook odroid-xu3
  rm -f description-pak Makefile postinstall-pak
}

package() {
  cd $pkgname

  mkdir -p "${pkgdir}"/{etc/udev/rules.d,etc/modprobe.d,etc/X11,etc/systemd/system,usr/bin,usr/lib/initcpio/install}

  install -m 0664 10-odroid.rules "${pkgdir}"/etc/udev/rules.d/
  install -m 0664 40-usb_modeswitch.rules "${pkgdir}"/etc/udev/rules.d/
  install -m 0664 blacklist-odroid.conf "${pkgdir}"/etc/modprobe.d/
  install -m 0664 xorg.conf "${pkgdir}"/etc/X11/xorg.conf
  install -m 0664 asound.conf "${pkgdir}"/etc/
  install -m 0664 odroid-tweaks.service "${pkgdir}"/etc/systemd/system/
  install -m 0755 odroid-tweaks "${pkgdir}"/usr/bin/
  install -m 0644 odroid-xu3 "${pkgdir}/usr/lib/initcpio/install/"
}
