
cmake_minimum_required(VERSION 3.2)

set(SOURCE_FILES benchio.f90 benchutil.f90 mpiio.f90 serial.f90 )


if ( ${USE_HDF5} )
    list(APPEND SOURCE_FILES hdf5.f90 )
    add_compile_definitions( USE_HDF5 )
endif()

set_source_files_properties(
  benchio.f90
  PROPERTIES Fortran_PREPROCESS ON
)


add_executable( benchio ${SOURCE_FILES})
target_link_libraries( benchio PUBLIC MPI::MPI_Fortran)

install(TARGETS benchio )