This approach and documentation is based upon https://github.com/balister/sdr-build

===============
Getting Started
===============

#. Clone the git repository:

  $ git clone https://github.com/bmagistro/sdr-build.git

#. Check out the appropriate branch:

  $ cd sdr-build
  $ git checkout -b dunfell-pi origin/dunfell-pi

#. Update the submodules:

  $ git submodule update --init

#. Initialize the build system:

  $ TEMPLATECONF=`pwd`/conf source ./poky/oe-init-build-env ./build

#. Build an image:

  $ bitbake gnuradio-image
