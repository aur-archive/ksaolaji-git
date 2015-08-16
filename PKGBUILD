#Contributor: Roberto Tarullo <nomeutente94@hotmail.it>
# Maintainer: vicky91 <vickypaiers@gmail.com>
pkgname=ksaolaji-git
pkgver=20120131
pkgrel=1
pkgdesc="KSaoLaJi cleans all sorts of waste things in your system."
arch=('i686' 'x86_64')
url="https://projects.kde.org/projects/playground/utils/ksaolaji"
license=('GPL')
depends=('kdebase-workspace')
makedepends=('cmake' 'automoc4' 'git')
conflicts=('ksaolaji')

_gitroot='git://anongit.kde.org/ksaolaji'
_gitname='ksaolaji'

build() {
  cd "${srcdir}"
  msg "Connecting to GIT server...."

  if [[ -d "${_gitname}" ]]; then
    cd "${_gitname}" && git pull origin
    msg "The local files are updated."
  else
    git clone "${_gitroot}" "${_gitname}"
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting build..."

  rm -rf "${srcdir}/${_gitname}-build"
  git clone "${srcdir}/${_gitname}" "${srcdir}/${_gitname}-build"
  cd "${srcdir}/${_gitname}-build"

  cmake . -DCMAKE_INSTALL_PREFIX=/usr
  make
}

package() {
  cd "${srcdir}/${_gitname}-build"
  make DESTDIR="${pkgdir}/" install
}

# vim:set ts=2 sw=2 et:

