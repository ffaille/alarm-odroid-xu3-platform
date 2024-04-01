This repository hosts a candidate odroid-xu3-platform PKGBUILD. It allows you to build the odroid-xu3-platform package which provides importants configuration and script files for ODROID XU3/XU4/HC1/HC2/MC1 (mainly from Hardkernel).

Le but de ce projet est de fournir les ajustements necessaires pour optimiser le fonctionnement de archlinux ARM. Maybe this code can be pushed into the official repository later...

Tested with XU4 only (don't have XU3/HC1/HC2/MC1). Work in progress. Feedback is welcome.

## Usage
* sudo pacman -S base-devel git
* git clone https://github.com/ffaille/alarm-odroid-xu3-platform.git
* cd alarm-odroid-xu3-platform
* makepkg --syncdeps --noconfirm --log
* sudo pacman -U ./odroid-xu3-platform-24.03-1-armv7h.pkg.tar.xz
