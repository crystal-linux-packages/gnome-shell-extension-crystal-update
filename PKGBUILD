# Maintainer:  echo -n 'TWF0dCBDLiA8bWF0dEBnZXRjcnlzdC5hbD4='     | base64 -d
# Contributor: echo -n 'TWljaGFsIFMuIDxtaWNoYWxAZ2V0Y3J5c3QuYWw+' | base64 -d
# Contributor: echo -n 'Um9iaW4gQy4gPHJjYW5kYXVAZ2V0Y3J5c3QuYWw+' | base64 -d

pkgname=gnome-shell-extension-crystal-update
_pkgname=crystal-update
pkgver=51
pkgrel=1
pkgdesc="Convenient indicator for Crystal Linux updates in GNOME Shell."
arch=('any')
url="https://github.com/crystal-linux/${_pkgname}"
license=('GPL3')
depends=('gnome-shell' 'ame')
conflicts=('gnome-shell-extensions-git')
source=("${pkgname}-${pkgver}.tar.gz::${url}/archive/v${pkgver}.tar.gz")
sha256sums=('4b680d65c3946e0f9fbe43dd5523fee7368209362eff28af225261226d1d7f6c')

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
