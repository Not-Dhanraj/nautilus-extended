# Contributor (maintainer of official Nautilus package): Fabian Bornschein <fabiscafe@archlinux.org>
# Contributor (maintainer of official Nautilus package): Jan Alexander Steffens (heftig) <heftig@archlinux.org>
# Contributor (contributor to official Nautilus package): Jan de Groot <jgc@archlinux.org>
# Contributor (original typeahead patch code): Jan de Groot <jgc@archlinux.org>
# Contributor (original package maintainer): Ian Hernández <badwolfie@archlinux.info>
# Contributor (current typeahead patch code): Xavier Claessens <xavier.claessens@collabora.com>
# Contributor (updated Xavier's typeahead patch for 43.2): Bryan Lai <bryanlais@gmail.com>
# Contributor (updated Xavier's typeahead patch for 44.1): DragoonAethis <dragoon@dragonic.eu>
# Contributor (updated Xavier's typeahead patch for 49.0): Kevin MacMartin <prurigro@gmail.com>
# Contributor (updated Xavier's typeahead patch for 50.0): Daniel Rudolf <archlinux.org@daniel-rudolf.de>
# Contributor (backspace patch code): Jeremy Bicha <jbicha@debian.org>
# Maintainer: Albert Vaca Cintora <albertvaka@gmail.com>

pkgbase=nautilus-extended
pkgname=(
  nautilus-extended
  libnautilus-extension-extended
)
packager="Albert Vaca Cintora <albertvaka@gmail.com>"
pkgver=51.1
pkgrel=19
pkgdesc="Nautilus Extended - GNOME file manager with per-folder grouping and type-ahead navigation"
url="https://github.com/Not-Dhanraj/nautilus-extended"
arch=(x86_64)
license=(GPL-3.0-or-later)
depends=(
  cairo
  dconf
  gdk-pixbuf2
  gexiv2
  glib2
  glibc
  glycin
  glycin-gtk4
  gnome-autoar
  gnome-desktop-4
  graphene
  gst-plugins-base-libs
  gstreamer
  gtk4
  gvfs
  hicolor-icon-theme
  icu
  libadwaita
  libcloudproviders
  libgcc
  libportal
  libportal-gtk4
  libx11
  localsearch
  pango
  tinysparql
  wayland
  xdg-user-dirs-gtk
)
makedepends=(
  appstream
  blueprint-compiler
  git
  glib2-devel
  gobject-introspection
  meson
  ninja
  pkgconfig
)
source=(
  "git+https://gitlab.gnome.org/GNOME/nautilus.git#tag=${pkgver/[a-z]/.&}"
  "git+https://gitlab.gnome.org/GNOME/libgxdp.git#commit=df896e3412b749947bc6f62a91a1aac8e6b6d19b"
  "0001-Add-configurable-Backspace-navigation.patch"
  "0002-Restore-typeahead-keyboard-navigation.patch"
  "0003-Add-per-folder-grouping-policy-and-list-sections.patch"
  "0004-Add-virtualized-grouped-icon-view.patch"
  "0005-Cycle-typeahead-matches-in-display-order.patch"
  "0006-Match-native-grouped-selection-styling.patch"
  "0007-Open-external-locations-in-new-windows.patch"
  "0008-Add-native-per-tab-dual-pane-navigation.patch"
  "0009-Test-native-dual-pane-navigation-and-lifecycle.patch"
  "0010-Round-location-entry-completion-popovers.patch"
  "0011-Honour-custom-bookmark-icons.patch"
  "post.install"
)
b2sums=(
  '13d7fde576d576c5903f1906263c8bd47e54bedcd88cd297077c4687b74eaef1519c458242ee1cb88ebad871411a44614404f12d21c9a7859d2b064c7e499dd1'
  'f5bd238c316a55784f97b1b7c8b498d3dfa727375cf8a1bf61f4771e306232b36752df8f61edb8d8c5da7c5e1a7acd8c0e85a53725af56e9b18b8dd1a6f284e0'
  '49f9b1845f12ee919731add9a221e07b049cdf0bc005595f01ae7ac01d92bee440b3927533268f087fc15f8d807c00913401fea8add8bf4949793eaf53404869'
  'e2dd881eed335af049891f7248eba81dc8bc15c1925fa9992f4a1f929874d9348b67dc79bc8c3a1d26dba07e4a12b785eaaf2a3bace4d2092765aa407cf7158d'
  'aa2a9d7a680476f3ba58a4af8495ab6961d99bd92ff4309dd02950d463a665c9c8bb83c1e9e6ca48199d45d19da500fc9bd437d56c1b9edd55e0ca9d634f6bd6'
  '0f9db37b8a0d30ec717ce5f7b302a99f14bc5d65d53a4966d1ff84f0993c563367df6021d1d17ea2ca1607da5c51f4170839786ba28314fdc2882c77ef9c7d15'
  '52ac4c55756fbd9fb9e317a11b271e09beb16dc0e71df0b132f2dd81f6a2ac3065158c1286570a615c6e6e9a506c4d4f39fa69aabf21a8221e5e7e80dedaab08'
  'd698023757b5882c4b412fa47f53628567ab00d058aa823c8967c9913d55e19a226d925c9ae618f9e7ab5bb214c97fc5f79175df399342ade563735c94cb28c4'
  '348e3b65d1ae55ee5ec1bec314a02fae2ffa5d8bcca82bc86d037434416605085d36a9d10d903544428ee6d46bc8ab3367258c932c205a6af63c557d871a3882'
  'b3ea754e688aee0d9dde52f7248e760dc026f6793f7d755ac855aeeaead7b51fcba028799bbe798e233413578e499316aaa961d3e121e3ead8b5dc65cc42536d'
  'b9f357793be1c55f0787f7f0d15017b6e2a4ac3be701d4284f062ed4b433b7288ac282e485c446928b7ece8265e3ed4011dd047c8eb792124785ae39f17b3fc0'
  'd04c542681e38331881cc6046b7b735a96d07ada68f0e14c572055103a4310c5b1b6e81291385736a3b8f949855089631ea62f3d91f5519a0d1430189de56b5f'
  '4d27e59c65783099185f6a789779f64a916dcc02ad93fabeb30c114a23e0b0bed001c19b5f772429a37d82ac820829df7c89028daee03ccd27645126282b6d31'
  '393f21868ed9e87d49b497745d50c7e99d7d09b86f21161e51cb1a812d15bbfb457343230b1c1a5d38d8edcc12e9337e86cb5684baa6e63d3b3b6c31ca2676c9'
)

prepare() {
  local p
  local -a added_paths

  cd nautilus

  # Apply declared patches only: srcdir may retain obsolete cached patch links.
  for p in "${source[@]}"; do
    [[ $p == *.patch ]] || continue
    # Older builds used patch(1), leaving these generated files untracked.
    # Clean only paths created by this declared patch, never the whole checkout.
    mapfile -t added_paths < <(
      git apply --summary "$srcdir/$p" | gawk '$1 == "create" && $2 == "mode" { print $4 }'
    )
    if (( ${#added_paths[@]} )); then
      git clean -f -- "${added_paths[@]}" || return
    fi
    # Stage patch outputs in this disposable source checkout so makepkg's next
    # forced Git checkout also removes files added by the series.
    git apply --index --whitespace=error "$srcdir/$p" || return
  done

  # Preserve the package's existing typeahead default independently of upstream.
  gawk -i inplace '/type-ahead-search/{c++;} c==1 && /true/{sub("true", "false"); c++;} 1' data/org.gnome.nautilus.gschema.xml

}

build() {
  local meson_options=(
    -D docs=false
    -D selinux=disabled
    -D tests=all
    -D werror=true
  )

  # Provide the pinned libgxdp source for Meson's fallback subproject.
  export MESON_PACKAGE_CACHE_DIR="$srcdir"

  arch-meson nautilus build "${meson_options[@]}"
  meson compile -C build
}

_pick() {
  local p="$1" f d; shift
  for f; do
    d="$srcdir/$p/${f#$pkgdir/}"
    mkdir -p "$(dirname "$d")"
    mv "$f" "$d"
    rmdir -p --ignore-fail-on-non-empty "$(dirname "$f")"
  done
}

package_nautilus-extended() {
  depends+=(
    libnautilus-extension.so
    libnautilus-extension-extended
  )
  optdepends=(
    'nautilus-sendto: Share files from the right click menu'
    'python-nautilus: Use extensions written in python'
  )
  install='post.install'
  conflicts=(nautilus nautilus-typeahead)
  replaces=(nautilus-typeahead)
  provides=(nautilus)
  groups=(gnome)

  meson install -C build --destdir "$pkgdir"

  cd "$pkgdir"

  _pick libne usr/include
  _pick libne usr/lib/{girepository-1.0,libnautilus-extension*,pkgconfig}
  _pick libne usr/share/gir-1.0
}

package_libnautilus-extension-extended() {
  pkgdesc="Extension interface for Nautilus"
  depends=(
    glib2
    glibc
    libgcc
  )
  conflicts=(libnautilus-extension libnautilus-extension-typeahead)
  replaces=(libnautilus-extension-typeahead)
  provides=(
    libnautilus-extension
    libnautilus-extension.so
  )

  mv libne/* "$pkgdir"
}

# vim:set sw=2 sts=-1 et:
