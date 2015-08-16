# Maintainer: rfk1ll <rfk1ll@outlook.com>
# Contributor: rfk1ll <rfk1ll@outlook.com>

pkgname=manarchy
pkgver=2013.11
pkgrel=2
pkgdesc="Collection of pentesting programs."
url="https://aur.archlinux.org/packages/manarchy/"
license=('GPL')
depends=('net-tools' 'sox' 'make' 'gcc' 'macchanger' 'nmap' 'wireshark-gtk' 'wxpython' 'iw' 'kismet' 'ettercap')
replaces=('aircrack-ng')
conflicts=('aircrack-ng')
arch=('any')
source=("http://download.aircrack-ng.org/aircrack-ng-1.2-beta1.tar.gz"
        "https://theharvester.googlecode.com/files/theHarvester-2.2a.tar.gz")
optdepends=('flite: a lightweight speech synthesis substitute'
            'hashcat: A multithreaded cross platform hash cracker.'
            'oclhashcat-plus-bin: Worlds fastest WPA cracker with dictionary mutation engine')
sha512sums=('e436443251d4c7895c6c2a71abde382222b2e4fc0856271dfb9825eb4b00383523dfcc0d8c1e8e807a5420cecf9f512adf8564e02cee70f03bd33db3568f5afe'
            '6d4892e92aadac0fe3ed6c0bdadc4b288f13fc5e99320299077d0a9b9766660a20785f4a579508d3f25a807832a296342e4c19085800a94a01b6f24bca1fb369')
package() {
    #creates neccesary directories
    mkdir -p $pkgdir/usr/share/theharvester
    mkdir -p $pkgdir/usr/bin

    #installs aircrack
    cd $srcdir/aircrack-ng-1.2-beta1
    make -C $srcdir/aircrack-ng-1.2-beta1
    make -C $srcdir/aircrack-ng-1.2-beta1 strip
    make -C $srcdir/aircrack-ng-1.2-beta1 DESTDIR="${pkgdir}" prefix=/usr install 

    #installs theharvester
    cd ${srcdir}/theHarvester-2.2a
    cp -rf $srcdir/theHarvester-2.2a/* $pkgdir/usr/share/theharvester
    ln -s /usr/share/theharvester/theHarvester.py "$pkgdir/usr/bin/theharvester"
    chmod +x $pkgdir/usr/share/theharvester/theHarvester.py
    sed -i '1s/$/2/' $pkgdir/usr/share/theharvester/theHarvester.py
}
