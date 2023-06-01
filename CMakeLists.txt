cmake_minimum_required(VERSION 3.2)

project( benchio LANGUAGES Fortran )
cmake_policy(SET CMP0074 NEW)

option(USE_HDF5 "Test HDF5 write" OFF)

if ( ${USE_HDF5} )
    find_package(HDF5 COMPONENTS Fortran HL)
endif()


find_package(MPI REQUIRED)

add_subdirectory(src)