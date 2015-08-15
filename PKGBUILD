# Maintainer: Benjamin Klettbach <b.klettbach@gmail.com>
# GitHub Repository (maybe for issues and improvements?): https://github.com/benklett/arch_package_google-chrome-extension-moonlight 

pkgname=google-chrome-extension-moonlight
pkgver=3.99.0.3
pkgrel=6
pkgdesc="Silverlight for Linux: a free plug-in"
arch=('i686' 'x86_64')
url="http://www.go-mono.com/moonlight"
license=('GPL' 'LGPL 2.0' 'MIT' 'Ms-PL' 'Apache 2.0')
depends=('google-chrome')
install=google-chrome-extension-moonlight.install
_arch=`uname -m`
if [ "$_arch" == "x86_64" ]
then
  _arch="x86_64"
else
  _arch="i586"
fi
source=("moonlight.crx"::"https://googledrive.com/host/0B0xVGvAbM6ZkVXlBTG9oLVBQVXc"
	      "external_extensions.patch")
noextract=("moonlight.crx")
if [ "$_arch" == "i586" ]
then
  source[0]=("moonlight.crx"::"https://googledrive.com/host/0B0xVGvAbM6ZkQzlDSFh4VVliM28")
  noextract=("moonlight.crx")

fi

md5sums=('0f1087a6e05f859595476b2f2b5167cf'
  '3aea5ee9761fc2345f84e442a14e967c')
if [ "$_arch" == "i586" ]
then
  md5sums[0]=('1fd14feb0734a74711a7b097e4158611')
fi

package() {
  cd "$pkgdir"
  
  if [ -f "/usr/bin/google-chrome-unstable" ]
	then
	_channel="unstable"
  elif [ -f  "/usr/bin/google-chrome-beta" ]
	then
	_channel="beta"
  else
	_channel="stable"
  fi

  if [ "$_channel" == "stable" ]
  then
  _chromeDefaultAppsPath="opt/google/chrome/default_apps"
  else
  _chromeDefaultAppsPath="opt/google/chrome-$_channel/default_apps"
  fi
  msg "You are on the $_channel channel of Google Chrome"

	install -D -m 644 "$srcdir/moonlight.crx" "$pkgdir/$_chromeDefaultAppsPath/novell-moonlight-$_arch.crx"
	install -D -m 644 "$srcdir/external_extensions.patch" "$pkgdir/$_chromeDefaultAppsPath/external_extensions.patch"
}

# vim:set ts=2 sw=2 et:
