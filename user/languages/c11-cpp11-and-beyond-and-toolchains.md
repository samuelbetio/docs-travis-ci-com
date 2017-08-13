### C11/C++11 (and Beyond) and Toolchain Versioning

If your project requires tools compatible with C11, C++11, or a more recent language standard, then it is likely that you will have to upgrade your compiler and/or build tools. This section covers specifically how to upgrade GCC, clang, and cmake; for other dependencies please see [Installing Dependencies](/user/installing-dependencies/).

#### GCC on Linux

Ubuntu 12.04 ships with GCC 4.6.3 and Ubuntu 14.04 ships with GCC 4.8.2.

Note that [GCC support for ISO C11 reached a similar level of completeness as ISO C99 in 4.9](https://gcc.gnu.org/wiki/C11Status) and that C++11 is feature-complete in 4.8.1, but [support for `<regex>` does not exist until 4.9](https://gcc.gnu.org/bugzilla/show_bug.cgi?id=53631).

To upgrade GCC to a more recent version, you will have to install the appropriate version from the `ubuntu-toolchain-r-test` source; see below for examples:

```yaml
matrix:
  include:
    # works on Precise and Trusty
    - os: linux
      addons:
        apt:
          sources:
            - ubuntu-toolchain-r-test
          packages:
            - g++-4.9
      env:
         - MATRIX_EVAL="CC=gcc-4.9 && CXX=g++-4.9"

    # works on Precise and Trusty