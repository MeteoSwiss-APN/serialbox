
if("${CMAKE_Fortran_COMPILER_ID}" MATCHES "Cray")
    set(CMAKE_Fortran_FLAGS "${CMAKE_Fortran_FLAGS} -hnoomp -eZ")
endif()


if(NOT "${CMAKE_Fortran_COMPILER_ID}" MATCHES "GNU")
    set(CMAKE_Fortran_FLAGS "${CMAKE_Fortran_FLAGS} -cpp")
endif()


if( "${CMAKE_Fortran_COMPILER_ID}" MATCHES "PGI")
    set(CMAKE_Fortran_FLAGS "${CMAKE_Fortran_FLAGS} -Mpreprocess")
endif()

set(
    SOURCES
    "m_ser_perturb.f90"
    "m_serialize.f90"
    "utils_ppser.f90"
)

add_library(
    FortranSer STATIC ${SOURCES}
)

install( TARGETS FortranSer DESTINATION lib/ )
