# Maintainer: Platon Pronko < platon7pronko at gmail dot com >

pkgname="cryptopro-csp-k1"
pkgver=5.0.11455
# pkgver is not allowed to contain forward slashes
_pkgver_patch="5"
_pkgver="$pkgver-$_pkgver_patch"
pkgrel=0
pkgdesc='CryptoPro CSP 4.0'
arch=('x86_64')
url='https://cryptopro.ru/products/cryptopro-csp'
license=('proprietary')
depends=(
    'glibc'
    'gcc-libs'
    'gtk2'
    'gdk-pixbuf2'
    'pango'
    'atk'
    'glib2'
    'curl'
    'pcsclite'
    'libxml2'
    'ccid'
    'acsccid'
)
makedepends=(
    'libarchive'
)
source=(
    'linux-amd64.tgz'
    'cades_linux_amd64.tar.gz'
)
md5sums=(
    'b87bbe581d2431c71b8ec79f4bf7303b'
    'e0fa664ce9fba1b38e8a6c2b3e0c419c'
)
install=cryptopro-csp-k1.install
options=(!strip)

package() {
    cd "$pkgdir"
    rpm2cpio "$srcdir/linux-amd64/lsb-cprocsp-base-${_pkgver}.noarch.rpm" | bsdtar -xf -
    rpm2cpio "$srcdir/linux-amd64/lsb-cprocsp-rdr-64-${_pkgver}.x86_64.rpm" | bsdtar -xf -
    rpm2cpio "$srcdir/linux-amd64/lsb-cprocsp-kc1-64-${_pkgver}.x86_64.rpm" | bsdtar -xf -
    rpm2cpio "$srcdir/linux-amd64/lsb-cprocsp-capilite-64-${_pkgver}.x86_64.rpm" | bsdtar -xf -
    rpm2cpio "$srcdir/linux-amd64/lsb-cprocsp-ca-certs-${_pkgver}.noarch.rpm" | bsdtar -xf -
    rpm2cpio "$srcdir/linux-amd64/lsb-cprocsp-devel-${_pkgver}.noarch.rpm" | bsdtar -xf -
    rpm2cpio "$srcdir/linux-amd64/cprocsp-rdr-gui-gtk-64-${_pkgver}.x86_64.rpm" | bsdtar -xf -
    rpm2cpio "$srcdir/linux-amd64/cprocsp-rdr-pcsc-64-${_pkgver}.x86_64.rpm" | bsdtar -xf -
    rpm2cpio "$srcdir/linux-amd64/cprocsp-rdr-jacarta-64-5.0.0.1148-4.x86_64.rpm" | bsdtar -xf -

    rpm2cpio "$srcdir/cades_linux_amd64/cprocsp-pki-2.0.0-amd64-cades.rpm" | bsdtar -xf -
    rpm2cpio "$srcdir/cades_linux_amd64/cprocsp-pki-2.0.0-amd64-plugin.rpm" | bsdtar -xf -

    rm -r "$pkgdir/etc/init.d/"
    mv "$pkgdir/tmp/" "$pkgdir/opt/cprocsp/tmp/"
    rm -r "$pkgdir/usr/lib64/"

    mkdir -p "$pkgdir/etc/ld.so.conf.d/"
    echo "/opt/cprocsp/lib/amd64" > "$pkgdir/etc/ld.so.conf.d/cryptopro-csp-k1.conf"
}
