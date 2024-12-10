## Benchmarking with BLAS and LAPACK

### NCCS

#### MKL

##### ifx

To run with `ifx` and MKL:

```
ml use -a /discover/swdev/gmao_SIteam/modulefiles-SLES15
ml comp/intel/2024.2.0-ifx

cmake -B build-ifx-mkl -DMKL=ON
cmake --build build-ifx-mkl

./build-ifx-mkl/dgemm
```

##### gfortran

To run with gfortran:

```
ml comp/gcc/13.2.0 lib/mkl/2024.2.0

cmake -B build-gfortran-mkl -DMKL=ON 
cmake --build build-gfortran-mkl

./build-gfortran-mkl/dgemm
```

#### AOCL

AOCL provides BLIS (for BLAS) and Flame (for LAPACK) libraries.

##### AOCC

To run with AOCC:

```
ml use -a /discover/swdev/gmao_SIteam/modulefiles-SLES15
ml load comp/aocc/4.1.0 lib/blis/aocc/5.0.0

cmake -B build-aocc-aocl -DAOCL=ON
cmake --build build-aocc-aocl

./build-aocc-aocl/dgemm
```

##### gfortran

To run with gfortran:

```
ml use -a /discover/swdev/gmao_SIteam/modulefiles-SLES15
ml load comp/gcc/13.2.0 lib/blis/gcc/5.0.0

cmake -B build-gfortran-aocl -DAOCL=ON
cmake --build build-gfortran-aocl

./build-gfortran-aocl/dgemm
```
