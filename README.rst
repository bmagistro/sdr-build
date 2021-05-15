This approach and documentation is based upon https://github.com/balister/sdr-build

===============
Getting Started
===============

#. Clone the git repository:

  $ git clone https://github.com/bmagistro/sdr-build.git

#. Check out the appropriate branch:

  $ cd sdr-build
  $ git checkout -b dunfell-ettus origin/dunfell-ettus

#. Update the submodules:

  $ git submodule update --init

#. Backport gcc-8.3

   There is a known issue in this release with fftw and the included version of gcc.
   This change has not been applied in testing yet but is included for reference.
   In addition, `GCCVERSION = "8.%"` will need to be added to the `build/local.conf` file.

   See https://github.com/EttusResearch/uhd/issues/396 for more details.

   $ tar -zxf backport-gcc-8.3.tgz

#. Initialize the build system:

  $ TEMPLATECONF=`pwd`/conf source ./poky/oe-init-build-env ./build

#. Build an image:

  $ bitbake gnuradio-image
