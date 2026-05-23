# Maintainer: artist for Artix Linux

pkgname=sonic-keybind-daemon
pkgver=6.6.5
pkgrel=1
_commit="4fbd9877efda72e5c46715de15edf20184534126"
pkgdesc='Daemon for Artix Linux providing Global Keyboard Shortcut (Accelerator) functionality'
arch=(x86_64)
url='https://github.com/Sonic-DE/sonic-globalacceld'
license=(LGPL-2.0-or-later)
depends=(glibc
         kconfig
         kcrash
         kdbusaddons
         kjobwidgets
         kservice
         libgcc
         libx11
         libxcb
         qt6-base
         sonic-frameworks-core-addons
         sonic-frameworks-io
         sonic-frameworks-keybind
         sonic-frameworks-windowsystem
         xcb-util-keysyms)
makedepends=(extra-cmake-modules)
groups=(sonicde)
conflicts=(kglobalacceld)
provides=(kglobalacceld)
replaces=(kglobalacceld)
makedepends+=(git)
source=("$pkgname-$pkgver::git+$url.git#commit=$_commit")

build() {
  cmake -B build  -S $pkgname-$pkgver \
    -DBUILD_TESTING=OFF \
    -DCMAKE_INSTALL_LIBEXECDIR=lib
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build

  rm -r $pkgdir/usr/lib/systemd
}

sha256sums=('4c8149da114ff364ed2c8a77a53eb44cc33e86b0a851c02cbe2635ed5ecceaaa')

