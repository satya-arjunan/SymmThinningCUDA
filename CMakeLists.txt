cmake_minimum_required(VERSION 3.10)
project(symm LANGUAGES CXX CUDA)

# Motocyte configuration
add_library(symm STATIC
  src/attachment.cu
  src/clique.cu
  src/neighbor.cu
  src/thinning.cu
  src/thinning_details.cu
  libs/io_shared.cpp)

find_package(HDF5 REQUIRED COMPONENTS CXX)
find_package(Boost COMPONENTS filesystem system REQUIRED)

include_directories(libs include . ${HDF5_INCLUDE_DIRS} ${Boost_INCLUDE_DIRS})

target_compile_features(symm PUBLIC cxx_std_11)
set_target_properties(symm PROPERTIES CUDA_SEPARABLE_COMPILATION ON)

add_executable(symm_test main.cu)
set_target_properties(symm_test PROPERTIES CUDA_SEPARABLE_COMPILATION ON)
target_link_libraries(symm_test PRIVATE symm ${Boost_LIBRARIES} ${HDF5_LIBRARIES})
