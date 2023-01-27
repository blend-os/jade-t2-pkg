# Maintainer: Rudra Saraswat <rs2009@ubuntu.com>
# Original maintainer: Crystal Linux Distribution Team <distribution@lists.getcryst.al>

pkgname=jade-t2
_pkgname=crystal-jade
pkgver=1.2.9
pkgrel=1
pkgdesc="Scriptable backend & TUI Installer for blendOS, with T2 support"
arch=('x86_64' 'aarch64')
url="https://github.com/blend-os/jade-t2"
license=('GPL3')
depends=('parted' 'arch-install-scripts')
provides=('jade')
conflicts=('jade')
makedepends=('cargo')
source=("git+${url}.git")
sha256sums=('SKIP')

prepare() {
    cd "jade-t2"
    cargo fetch --locked --target "${CARCH}-unknown-linux-gnu"
}

build() {
    cd "jade-t2"
    export RUSTUP_TOOLCHAIN=stable
    export CARGO_TARGET_DIR=target
    cargo build --frozen --release --all-features
}

package() {
    cd "jade-t2"
    install -Dm 755 "target/release/${_pkgname}" "${pkgdir}/usr/bin/${_pkgname}"
}
