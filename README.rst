This approach and documentation is based upon https://github.com/balister/sdr-build

===============
Getting Started
===============

#. Clone the git repository:

  $ git clone https://github.com/bmagistro/sdr-build.git

#. Check out the appropriate branch:

  $ cd sdr-build
  $ git checkout -b zeus-ettus origin/zeus-ettus

#. Update the submodules:

  $ git submodule update --init

#. Backport gcc-8.3

   There is a known issue in this release with fftw and the included version of gcc.

   See https://github.com/EttusResearch/uhd/issues/396 for more details.

   $ tar -zxf backport-gcc-8.3.tgz

#. Remove conflicting kernel patch

   Another developer has identified a potential issue with an included patch and requested
   additional information from NI.  In the interim the patch should be removed. Technically
   it should only need to be removed from `core.scc` but we remove the file too to ensure
   it isn't referenced somewhere else we missed.

   See https://lists.ettus.com/empathy/thread/ZDFCMZN4HB2HGE7PH2CG7BKU67SD3M4X for more details.

   $ rm meta-ettus/meta-ettus-core/recipes-kernel/linux/linux-yocto-5.2/0019-spi-cadence-Revert-cs-gpio-using-descriptors.patch
   $ sed -ie '/0019-spi-cadence-Revert-cs-gpio-using-descriptors.patch/d' meta-ettus/meta-ettus-core/recipes-kernel/linux/linux-yocto-5.2/core.scc

#. Initialize the build system:

  $ TEMPLATECONF=`pwd`/conf source ./poky/oe-init-build-env ./build

#. Build an image:

  $ bitbake gnuradio-image
