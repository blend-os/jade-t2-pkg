# Maintainer: Rudra Saraswat <rs2009@ubuntu.com>
# Original maintainer: Crystal Linux Distribution Team <distribution@lists.getcryst.al>

pkgname=jade
_pkgname=crystal-jade
pkgver=1.2.9
pkgrel=1
pkgdesc="Scriptable backend & TUI Installer for blendOS"
arch=('x86_64' 'aarch64')
url="https://git.getcryst.al/rs2009/jade"
license=('GPL3')
depends=('parted' 'arch-install-scripts')
makedepends=('cargo')
source=("git+${url}.git")
sha256sums=('SKIP')

prepare() {
    cd "jade"
    cargo fetch --locked --target "${CARCH}-unknown-linux-gnu"
}

build() {
    cd "jade"
    export RUSTUP_TOOLCHAIN=stable
    export CARGO_TARGET_DIR=target
    cargo build --frozen --release --all-features
}

package() {
    cd "jade"
    install -Dm 755 "target/release/${_pkgname}" "${pkgdir}/usr/bin/${_pkgname}"
}
