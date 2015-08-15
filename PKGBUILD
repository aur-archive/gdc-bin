# Maintainer: Anntoin Wilkinson <anntoin@gmail.com>
# Contributor: Shirakawasuna <Shirakawasuna@gmail.com>

pkgname=gdc-bin
pkgver=0.24
pkgrel=5
pkgdesc="GDC, Digital Mars D Programing Language (DMD) frontend for GCC"
arch=('i686' 'x86_64')
url="http://dgcc.sourceforge.net/"
license=('GPL')
provides=('gdc')
depends=('gcc-libs>=4.1.2' 'perl')
conflicts=('gdc' 'gdc-tango' 'gdc1-tango-svn' 'gdc1-hg')
source=(http://downloads.sourceforge.net/project/dgcc/gdc/${pkgver}/gdc-${pkgver}-${CARCH}-linux-gnu-gcc-4.1.2.tar.bz2)
md5sums=('f4fecc6a5059f8f3de56b65cc4589bbd')

package() {
  # Create Directories
  install -d ${pkgdir}/usr/{bin,lib,include,share/{man/man1,doc/gdc}}

  cd ${srcdir}/gdc

  # Install man pages and documentation
  install -m644 -t ${pkgdir}/usr/share/man/man1/ man/man1/{gdc.1,gdmd.1}
  install -m644 -t ${pkgdir}/usr/share/doc/gdc/ share/doc/gdc/{GDC.html,README.GDC}

  # Install Binaries
  install -m755 -t ${pkgdir}/usr/bin/ bin/{gdc,gdmd} libexec/*/*/*/{cc1d,collect2}

  # Install Library
  if [ ${CARCH} == 'x86_64' ]; then
    install -m644 -t ${pkgdir}/usr/lib/ lib64/libgphobos.a 
  else
    install -m644 -t ${pkgdir}/usr/lib/ lib/libgphobos.a 
  fi
  
  # Install other resources
  find {include/d,lib/gcc} -type f -exec install -Dm644 {} ${pkgdir}/usr/{} \;
}

# vim:set ts=2 sw=2 et:
