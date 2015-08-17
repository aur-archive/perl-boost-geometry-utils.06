# Contributor: Swift Geek <swiftgeek «at» gmail.com>
pkgname=perl-boost-geometry-utils.06
pkgver=0.06
pkgrel=1
pkgdesc="Boost::Geometry::Utils - Bindings for the Boost Geometry library"
arch=('any')
url="http://search.cpan.org/~aar/Boost-Geometry-Utils-${pkgver}/"
license=('GPL' 'PerlArtistic')
depends=('perl>=5.10.0' 'perl-module-build-withxspp' 'perl-extutils-typemaps-default' 'perl-extutils-xspp')
makedepends=()
provides=('perl-boost-geometry-utils')
conflicts=('perl-boost-geometry-utils')
replaces=()
backup=()
options=(!emptydirs)
install=
source=("http://search.cpan.org/CPAN/authors/id/A/AA/AAR/Boost-Geometry-Utils-${pkgver}.tar.gz")
md5sums=('e73373480a3861c3f0cd061079241eab')

prepare() {
  export _src_dir="$srcdir/Boost-Geometry-Utils-$pkgver"
  # Setting these env variables overwrites any command-line-options we don't want...
  export PERL_MM_USE_DEFAULT=1 PERL_AUTOINSTALL=--skipdeps \
    PERL_MM_OPT="INSTALLDIRS=vendor DESTDIR='$pkgdir'" \
    PERL_MB_OPT="--installdirs vendor --destdir '$pkgdir'" \
    MODULEBUILDRC=/dev/null
}

build() {
  cd "$_src_dir"
  /usr/bin/perl Build.PL 
  ./Build 
}

check () {
  cd "$_src_dir"
  ./Build test
}

package () {
  cd "$_src_dir"
  ./Build install

  # remove perllocal.pod and .packlist
  find "$pkgdir" -name .packlist -o -name perllocal.pod -delete
}

