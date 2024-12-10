cmake_minimum_required(VERSION 3.27)

project(dgemm
  LANGUAGES Fortran C
)

find_package(OpenMP REQUIRED)
option(MKL "Use MKL" OFF)
option(AOCL "Use AOCL" OFF)
if(MKL)
  set(BLA_VENDOR Intel10_64lp)
endif()
if(AOCL)
  set(BLA_VENDOR AOCL)
endif()
find_package(BLAS REQUIRED)
find_package(LAPACK REQUIRED)

add_executable(dgemm dgemm.F90)
target_link_libraries(dgemm PRIVATE OpenMP::OpenMP_Fortran BLAS::BLAS LAPACK::LAPACK)

