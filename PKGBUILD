# Maintainer: Yunhui Fu <yhfudev@gmail.com>

pkgname=aria2c-daemon
pkgver=0.1
pkgrel=1
pkgdesc='Daemonize aria2c'
license=('GPL3')
arch=(any)
depends=('aria2')
conflicts=('aria2-daemon-svn')
replaces=('aria2-daemon-svn')
makedepends=('git')
url='https://github.com/yhfudev/aria2c-daemon-arch.git'
install=$pkgname.install
source=( aria2c-env.conf aria2c.conf aria2cd.service )
md5sums=('9d9a3efc3c7e44fe945866ee6b45a2dc'
         'a3a455ba5c447b82e44072dbef267cc6'
         '90e550eca6f8524ad4651bd0b31be1d8')

_giturl='https://github.com/yhfudev/aria2c-daemon-arch.git'
_gitdir='aria2c-daemon-git'

build() {
	msg 'Cloning GIT repository...'
	cd "${srcdir}"
	cd ${srcdir}
	if [ -d ${_gitdir}/.git ]; then
		(cd ${_gitdir} && git pull origin)
	else
		(git clone ${_giturl} ${_gitdir})
	fi
	msg 'GIT repository downloaded...'
}

package() {
	install -D -m644 "${srcdir}/${_gitdir}/aria2c-env.conf" "${pkgdir}/etc/conf.d/aria2c-env.conf"
	install -D -m600 "${srcdir}/${_gitdir}/aria2c.conf"     "${pkgdir}/etc/conf.d/aria2c.conf"
	install -D -m755 "${srcdir}/${_gitdir}/aria2cd.service" "${pkgdir}/etc/systemd/system/aria2cd.service"
}

