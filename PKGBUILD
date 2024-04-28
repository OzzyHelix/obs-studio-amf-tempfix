# Maintainer: José Miguel Sarasola <jmsaraur@gmail.com>
# Contributor: Jonathan Steel <jsteel at archlinux.org>
# Contributor: Benjamin Klettbach <b.klettbach@gmail.com>


pkgname=obs-studio-amf
pkgver=30.0.2
pkgrel=7
pkgdesc="Free, open source software for live streaming and recording. Includes new AMF encoding patch & browser plugin"
arch=('x86_64')
url="https://obsproject.com"
license=('GPL2')
depends=(
  "alsa-lib"
  "curl"
  "fontconfig"
  "freetype2"
  "ftl-sdk"
  "gcc-libs"
  "glib2"
  "glibc"
  "jansson"
  "libgl"
  "libpipewire"
  "libpulse"
  "librist"
  "libva"
  "libx11"
  "libxcb"
  "libxcomposite"
  "libxkbcommon"
  "mbedtls"
  "pciutils"
  "rnnoise"
  "speexdsp"
  "srt"
  "util-linux-libs"
  "wayland"
  "x264"
  "zlib"
  "libdatachannel"
  'amf-amdgpu-pro'
  'linux-firmware'
  'cef-minimal-obs-bin'
)
makedepends=(
  'cmake'
  'git'
  'libfdk-aac'
  'libxcomposite'
  "vlc-luajit"
  'pipewire'
  'python'
  'qt6-wayland'
  "qrcodegencpp-cmake"
  "qt6-base"
  "qt6-svg"
  'sndio'
  'swig'
  'wayland'
  'x264'
  'xdg-desktop-portal'
  'nlohmann-json'
  'websocketpp'
  'asio'
)
optdepends=('libfdk-aac: FDK AAC codec support'
            'libva-intel-driver: ffmpeg hardware encoding'
            'libva-mesa-driver: ffmpeg hardware encoding'
            'libxcomposite: xcomposite capture support'
            'luajit: scripting support'
            'onevpl-intel-gpu: quicksync hardware Encoding'
            'pipewire: pipewire capture support'
            'python: scripting support'
            'sndio: Sndio input client'
            'v4l2loopback-dkms: virtual camera support'
            'vlc: vlc media source support'
            'xdg-desktop-portal: pipewire capture support'
)
provides=("obs-studio=$pkgver" "obs-websocket" "obs-browser")
conflicts=("obs-studio" "obs-websocket" "obs-browser" "obs-linuxbrowser")
source=("obs-studio::git+https://github.com/obsproject/obs-studio.git#tag=$pkgver"
        "obs-browser::git+https://github.com/obsproject/obs-browser.git"
        "obs-websocket::git+https://github.com/obsproject/obs-websocket.git"
        fix_python_binary_loading.patch
        obs-amf-patch.patch)
sha256sums=('5a644b18917417c67314614b32f49df375cdd7fb067e8c28540ac21ee7e69113'
            'SKIP'
            'SKIP'
            'bdfbd062f080bc925588aec1989bb1df34bf779cc2fc08ac27236679cf612abd'
            '5c3a9c11136c3d146f7e3c41b4bee5ee821c0d22298c433cc99a0cfecdd5c4d0')

prepare() {
  cd obs-studio

  git config submodule.plugins/obs-browser.url $srcdir/obs-browser
  git config submodule.plugins/obs-websocket.url $srcdir/obs-websocket
  git -c protocol.file.allow=always submodule update

  patch -Np1 < "$srcdir"/fix_python_binary_loading.patch
  patch -Np1 < "$srcdir"/obs-amf-patch.patch
}

build() {
  cmake -B build -S obs-studio \
    -DCMAKE_INSTALL_PREFIX="/usr" \
    -DCMAKE_INSTALL_LIBDIR=lib \
    -DBUILD_BROWSER=ON \
    -DCEF_ROOT_DIR="/opt/cef-obs" \
    -DENABLE_VST=ON \
    -DENABLE_AJA=OFF \
    -DENABLE_JACK=ON \
    -DENABLE_LIBFDK=ON \
    -DOBS_VERSION_OVERRIDE="$pkgver-$pkgrel" \
    -DCALM_DEPRECATION=ON \
    -Wno-dev
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
