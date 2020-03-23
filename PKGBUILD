# Maintainer: Platon Pronko < platon7pronko at gmail dot com >

pkgname="cryptopro-csp-dev"
pkgver=5.0.11729
# pkgver is not allowed to contain forward slashes
_pkgver_patch="6"
_pkgver="$pkgver-$_pkgver_patch"
pkgrel=1
pkgdesc='CryptoPro CSP 5.0 R2'
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
md5sums=('3c8923525f86fa51f7aa890cd66b0f4d'
         'e0fa664ce9fba1b38e8a6c2b3e0c419c')
install=cryptopro-csp-dev.install
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
    rpm2cpio "$srcdir/linux-amd64/cprocsp-rdr-jacarta-64-5.0.0.1170-4.x86_64.rpm" | bsdtar -xf -

    rpm2cpio "$srcdir/cades_linux_amd64/cprocsp-pki-2.0.0-amd64-cades.rpm" | bsdtar -xf -
    rpm2cpio "$srcdir/cades_linux_amd64/cprocsp-pki-2.0.0-amd64-plugin.rpm" | bsdtar -xf -

    rm -r "$pkgdir/etc/init.d/"
    mv "$pkgdir/tmp/" "$pkgdir/opt/cprocsp/tmp/"
    rm -r "$pkgdir/usr/lib64/"

    mkdir -p "$pkgdir/etc/ld.so.conf.d/"
    echo "/opt/cprocsp/lib/amd64" > "$pkgdir/etc/ld.so.conf.d/cryptopro-csp-dev.conf"
}
