pkgname=franz
pkgver=4.0.1
pkgrel=1
pkgdesc='A free messaging app for WhatsApp, Facebook Messenger, Telegram, Slack and more.'
arch=('i686' 'x86_64')
depends=('alsa-lib' 'gconf' 'gtk2' 'libnotify' 'libxtst' 'nss')
url='http://meetfranz.com/'
license=('custom')
_file_i686="Franz-linux-ia32-$pkgver.tgz"
_file_x86_64="Franz-linux-x64-$pkgver.tgz"
source=("$pkgname.desktop" "$pkgname.png")
source_i686=("https://github.com/imprecision/franz-app/releases/download/$pkgver/$_file_i686")
source_x86_64=("https://github.com/imprecision/franz-app/releases/download/$pkgver/$_file_x86_64")
sha256sums=('c63052b7ada73dbc984f55afc6d0ad937bf57ae5b0b41b560ef46937afeb81c5'
            '6e761371afadf155b8bc25e94fd7de371c16130a87338300e5800924916a7a28')
sha256sums_i686=('b0cc5c68f74ba0250efd9186b41f9db039fc1670e9abc78704b16c1db12b12d8')
sha256sums_x86_64=('965ff28c65fe7b5be53c6691f610ecb529ff653f355f9bc44c085bde5246dc75')
noextract=("$_file_i686" "$_file_x86_64")

[[ "$CARCH" = "i686" ]] && _file="$_file_i686"
[[ "$CARCH" = "x86_64" ]] && _file="$_file_x86_64"

package() {
    install -d "$pkgdir"/{opt/$pkgname,usr/{bin,share/{licenses/$pkgname,pixmaps}}}
    bsdtar -xf "$srcdir/$_file" -C "$pkgdir/opt/$pkgname"
    ln -sf /opt/$pkgname/Franz "$pkgdir/usr/bin/$pkgname"

    install -Dm644 "$srcdir/$pkgname.png" "$pkgdir/usr/share/pixmaps/franz.png"

    install -Dm644 "$pkgdir/opt/$pkgname/LICENSE" \
        "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
    install -Dm644 "$pkgdir/opt/$pkgname/LICENSES.chromium.html" \
        "$pkgdir/usr/share/licenses/$pkgname/LICENSES.chromium.html"

    install -Dm644 "$srcdir/$pkgname.desktop" \
        "$pkgdir/usr/share/applications/$pkgname.desktop"

    # fix ownership
    chown root:root -R "$pkgdir/opt/$pkgname"

    # clean unneeded resources
    rm -rf "$pkgdir/opt/$pkgname/resources/app.asar.unpacked/node_modules"
}
