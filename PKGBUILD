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

pkgbase=nautilus-typeahead
pkgname=(
  nautilus-typeahead
  libnautilus-extension-typeahead
)
packager="Albert Vaca Cintora <albertvaka@gmail.com>"
pkgver=51.1
pkgrel=1
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
  "0001-Restore-backspace-for-going-to-parent-folder.patch"
  "0002-Restore-typeahead-support-for-keyboard-navigation.patch"
  "0003-Add-per-folder-grouping-policy-and-list-sections.patch"
  "0004-Add-virtualized-grouped-icon-view.patch"
  "0005-Cycle-typeahead-matches-in-display-order.patch"
  "post.install"
)
b2sums=(
  '13d7fde576d576c5903f1906263c8bd47e54bedcd88cd297077c4687b74eaef1519c458242ee1cb88ebad871411a44614404f12d21c9a7859d2b064c7e499dd1'
  'f5bd238c316a55784f97b1b7c8b498d3dfa727375cf8a1bf61f4771e306232b36752df8f61edb8d8c5da7c5e1a7acd8c0e85a53725af56e9b18b8dd1a6f284e0'
  'b9af0c0c3c9e233d13a1287d5f5fa7b159cff5532ccd589791c4916f34c69cc27755207cbec1c0a87ccce7a273d3e7d3f9c1d756e2a6bedae0124f30a214fef0'
  'a04d4c2311c2760850411722c369acb16702464045f3302644d5f086aa5c87bb7eba2fc631e551405793bbe3cf696a7e7397add73a1214f8bfcc2789a1aa17ff'
  '5528cda10721118b0b86374a673a67ab1872f53d155ea0fde3018705b658560b68c750f6f8991142eefe2ff92cd16bc00fe25abb3ecf3bf7ed62f8ef5a4fb839'
  'ccf465d9133a59d5bec5236f35ad06f5a9d9ff7287d939147b3e0d7ba0a37b5aa05f5fe0c9da9631e72a59537e5150e3f0738329cbad6819834b257649a14421'
  '9606361e2de3a92d0061ed979e926893b8a4c0e020f5dacdafe1b755a3cf4680f28b4c721fc4cce95f4493d3fddbdd575fe4c390758c8c3ee07b4b309827ef46'
  '7ba197c2e65108ab49c1795c44264181c3c6b8f7d6641d1b1353690202c915e0aed574f45467924f6fb67a65f9487a3c0e24252633066e25b4d2c0dac3609245'
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
    git apply --index "$srcdir/$p" || return
  done

  # Enable typeahead behavior by default
  gawk -i inplace '/type-ahead-search/{c++;} c==1 && /true/{sub("true", "false"); c++;} 1' data/org.gnome.nautilus.gschema.xml

}

build() {
  local meson_options=(
    -D docs=false
    -D selinux=disabled
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

package_nautilus-typeahead() {
  depends+=(
    libnautilus-extension.so
    libnautilus-extension-typeahead
  )
  optdepends=(
    'nautilus-sendto: Share files from the right click menu'
    'python-nautilus: Use extensions written in python'
  )
  install='post.install'
  conflicts=(nautilus)
  provides=(nautilus)
  groups=(gnome)

  meson install -C build --destdir "$pkgdir"

  cd "$pkgdir"

  _pick libne usr/include
  _pick libne usr/lib/{girepository-1.0,libnautilus-extension*,pkgconfig}
  _pick libne usr/share/gir-1.0
}

package_libnautilus-extension-typeahead() {
  pkgdesc="Extension interface for Nautilus"
  depends=(
    glib2
    glibc
    libgcc
  )
  conflicts=(libnautilus-extension)
  provides=(
    libnautilus-extension
    libnautilus-extension.so
  )

  mv libne/* "$pkgdir"
}

# vim:set sw=2 sts=-1 et:
