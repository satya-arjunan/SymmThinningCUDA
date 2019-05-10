# SymmThinningCUDA
Unix version with CMake

### On Mac OS
1. brew install hdf5
1. brew install boost
1. brew install cmake

1. mkdir build
1. cd build
1. cmake ..
1. make -j
1. cp -r ../oldH5 .
1. cp -r ../newH5 .
1. ./symm_test
