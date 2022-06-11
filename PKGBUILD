#!/bin/bash

# Based on original packaging by Marcell Meszaros < marcell.meszaros AT runbox.eu >, Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>, Allan McRae <allan@archlinux.org> and Sarah Hay <sarahhay@mb.sympatico.ca>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors

# Maintainer: Ross Clark <https://github.com/Archiv8/perl-sdl/discussions>
# Contributor: Ross Clark <https://github.com/Archiv8/perl-sdl/discussions>

_cpan_author="FROGGS"
_relname="SDL"

pkgname=perl-sdl
pkgver=2.548
pkgrel=7
pkgdesc="Simple DirectMedia Layer for Perl"
arch=(
  "x86_64"
  )
license=(
  LGPL
  )
url="https://metacpan.org/dist/SDL"
depends=(
  "perl>=5.008"
  "perl-alien-sdl>=1.446"
  "perl-cpan>=1.92"
  "perl-file-sharedir>=1.00"
  "perl-tie-simple"
  "perl-scalar-list-utils"
  "sdl_net"
  "sdl_ttf"
  "sdl_image"
  "sdl_mixer"
  "sdl_gfx"
  "sdl_pango"
  "smpeg"
)
makedepends=(
  "perl-capture-tiny"
  "perl-extutils-cbuilder"
  "perl-module-build>=0.40"
  "perl-test-most>=0.21"
  "perl-test-simple>=0.88"
)
options=(
  "!emptydirs"
  )
_tarname="${_relname}-${pkgver}"
source=(
  "https://cpan.metacpan.org/authors/id/${_cpan_author::1}/${_cpan_author::2}/$_cpan_author/${_tarname}.tar.gz"
  )
sha512sums=(
  "bafc49dddb7e592861f822920915c73bf0c5eea3a6c567623b48a2332c7644caf1451e457545e6666adea5e314b23bcd85a3f3a52c770abfd498c0e4c0feae85"
  )

build() {

  cd ${_tarname}
  
  # Perl selects the proper CFLAGS set for binary modules
  unset CFLAGS
  
  # install module in vendor directories
  perl Build.PL installdirs=vendor
  perl Build
}

check() {
  
  cd ${_tarname}
  
  perl Build test || true
}

package() {
  
  cd ${_tarname}
  
  perl Build install destdir="${pkgdir}"
}
