# Maintainer: matt <matt[at]getcryst[dot]al>

# Contributor: skrewball <aur at joickle dot com>
# Contributor: Llewelyn Trahaearn <WoefulDerelict at GMail dot com>
# Contributor: Michael Wendland <dev at michiwend dot com>

_pkgname=crystal-update
pkgname=gnome-shell-extension-crystal-update
pkgver=49
pkgrel=1
pkgdesc="Convenient indicator for Crystal Linux updates in GNOME Shell."
arch=('any')
url="https://github.com/crystal-linux/crystal-update"
license=('GPL3')
depends=('fakeroot' 'gnome-shell' 'pacman-contrib')
conflicts=('gnome-shell-extensions-git')
source=("${pkgname}-${pkgver}.tar.gz::${url}/archive/v${pkgver}.tar.gz")
sha256sums=('dd64d45f2e2d258c8e042eeaa7a6c110fec951eec4bb2116f2f47c4b551a9334')


package() {
  cd "${_pkgname}-${pkgver}"
  local _extname=$(grep -Po '(?<="uuid": ")[^"]*' metadata.json)
  local _destdir="${pkgdir}/usr/share/gnome-shell/extensions/${_extname}"

  install -Dm644 -t "${_destdir}" metadata.json *.js *.xml *.css
  cp -r --no-preserve=ownership,mode icons "${_destdir}"
  install -Dm644 -t "${pkgdir}/usr/share/glib-2.0/schemas/" schemas/*.xml

  cd locale
  for locale in */
    do
      install -Dm644 -t "${pkgdir}/usr/share/locale/${locale}/LC_MESSAGES" "${locale}/LC_MESSAGES"/*.mo
    done
}
