# Contributor: Det <nimetonmaili at gmail a-dot com>
# Contributor: Lee Jackson <tomoe AT lbjackson DOTCOM>
# Based on [extra]'s wine

pkgname=bin32-wine-suse
pkgver=1.3.37
pkgrel=2
_suserel=$pkgrel.1
pkgdesc="A compatibility layer for running Windows programs - openSUSE i586 build"
url="http://en.opensuse.org/Wine"
install=$pkgname.install
arch=('x86_64')
license=('LGPL')
depends=('lib32-fontconfig' 'lib32-mesa' 'lib32-libxcursor' 'lib32-libxrandr' 'lib32-libxdamage' 'lib32-libxi' 'lib32-gettext' 'lib32-gnutls' 'desktop-file-utils')
optdepends=('lib32-giflib' 'lib32-libpng' 'lib32-libldap' 'lib32-lcms' 'lib32-libxml2' 'lib32-mpg123' 'lib32-openal' 'lib32-v4l-utils' 'lib32-libpulse' 'lib32-alsa-plugins' 'lib32-alsa-lib' 'wine_gecko')
provides=("wine=$pkgver" 'winetricks')
conflicts=('wine' 'winetricks-svn')
source=(http://download.opensuse.org/repositories/Emulators:/Wine/openSUSE_Factory/i586/wine-$pkgver-$_suserel.i586.rpm
        http://download.opensuse.org/repositories/Emulators:/Wine/openSUSE_Factory/i586/wine-devel-$pkgver-$_suserel.i586.rpm)
md5sums=(`curl -s $source.md5 | cut -d " " -f1`
         `curl -s ${source[1]}.md5 | cut -d " " -f1`)

# -- Reduce compression time -- 
# Comment, if you want a regular .pkg.tar.xz package instead
PKGEXT='.pkg.tar'

package() {
  msg2 "Cleaning up unnecessary desktop entries"
  rm -f usr/share/applications/wine-*

  msg2 "Re-arranging docs"
  mv usr/share/doc/{packages/wine,wine}
  rm -rf usr/share/doc/packages

  msg2 "Moving everything in place"
  mv usr/ "$pkgdir/"
}
