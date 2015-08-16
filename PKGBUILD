# Contributor: Ben Alex <ben.alex@acegi.com.au>

pkgname=ibconnect-git
pkgver=0.20140428190746
pkgrel=1
pkgdesc="Interactive Brokers account balance and portfolio history server"
arch=('any')
url="https://github.com/benalexau/ibconnect-aur"
license=GPL3
depends=('ib-controller' 'postgresql')
makedepends=('git' 'go')
backup=('etc/ibconnect')
source=('ibconnect'
	'ibconnect.service')
md5sums=('4e53fa140e0fe264113ed29f9200f98b'
         '51251067a2490dd780b6e74013234634')

build() {
  GOPATH="${srcdir}" go get -v -x github.com/benalexau/ibconnect/ibcd
}

package() {
  install -Dm755 ${srcdir}/bin/ibcd ${pkgdir}/usr/bin/ibcd
  install -Dm644 ${srcdir}/ibconnect ${pkgdir}/etc/ibconnect
  install -Dm644 ${srcdir}/ibconnect.service ${pkgdir}/usr/lib/systemd/system/ibconnect.service
  install -Dm644 ${srcdir}/src/github.com/benalexau/ibconnect/db/dbconf.yml ${pkgdir}/usr/share/ibconnect/db/dbconf.yml
  mkdir -p ${pkgdir}/usr/share/ibconnect/db/migrations
  install -m644  ${srcdir}/src/github.com/benalexau/ibconnect/db/migrations/* ${pkgdir}/usr/share/ibconnect/db/migrations
}
