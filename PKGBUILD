# Maintainer: Josh VanderLinden <arch@cloudlery.com>
pkgname=pp-git
pkgver=20130125
pkgrel=1
pkgdesc="Simple wrapper around dd to show approximate progress during a dump"
arch=('any')
url="https://bitbucket.org/instarch/pp"
license=('MIT')
groups=()
depends=('coreutils' 'python2')
makedepends=('git')
source=('LICENSE')
md5sums=('3d9d229ee85c5a5bae93cff0033f66d9')

_gitroot=${url}
_gitname=pp

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [[ -d "$_gitname" ]]; then
    cd "$_gitname" && git pull origin
    msg "The local files are updated."
  else
    git clone "$_gitroot" "$_gitname"
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting build..."

  rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"
  cd "$srcdir/$_gitname-build"
}

package() {
  cd "$srcdir/$_gitname-build"
  install -D pp.py -m755 "${pkgdir}/usr/bin/pp"
  install -D LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

# vim:set ts=2 sw=2 et:
