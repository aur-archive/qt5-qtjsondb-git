# Maintainer: Sergio Correia <sergio.correia@uece.net>
# Contributor: Anselmo L. S. Melo <anselmolsm@gmail.com>

pkgname=qt5-qtjsondb-git
pkgver=20130303
pkgrel=1
pkgdesc="Qt 5: qtjsondb module"
groups=('qt5' 'qt5-addons')
arch=('i686' 'x86_64')
url="https://qt.gitorious.org/qt/qtjsondb"
license=('LGPL')
depends=('libedit' 'qt5-qtbase-git' 'qt5-qtdeclarative-git')
makedepends=('git')
options=('!libtool')
source=()
md5sums=()

_gitroot="git://gitorious.org/qt/qtjsondb.git"
_gitname=qt5-qtjsondb
_gitbranch=master

build() {
    if [ ! -d "${_gitname}" ]; then
        git clone ${_gitroot} -b ${_gitbranch} --depth 1 ${_gitname} && cd ${_gitname}
    else
        cd ${_gitname} && git reset --hard && git pull origin && git clean -dfx
    fi

    msg "GIT checkout done."

    /opt/qt5/bin/qmake
    make
}

package() {
    cd "${_gitname}"

    make INSTALL_ROOT="${pkgdir}" install
}
