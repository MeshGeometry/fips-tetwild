if (NOT FIPS_IMPORT)
    cmake_minimum_required(VERSION 2.8)
    get_filename_component(FIPS_ROOT_DIR "../fips" ABSOLUTE)
    include("${FIPS_ROOT_DIR}/cmake/fips.cmake")
    fips_setup()
    fips_project(fips-libigl)
endif()

if (MSVC)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /MP /bigobj") ### Enable parallel compilation
    string(REPLACE "/WX" "" CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS}")
    string(REPLACE "/WX" "" CMAKE_C_FLAGS "${CMAKE_C_FLAGS}")
endif(MSVC)


set(FIPS_RTTI ON CACHE BOOL "Enable C++ RTTI" FORCE)
set(FIPS_EXCEPTIONS ON CACHE BOOL "Enable C++ exceptions" FORCE)

# add_subdirectory(TetWild/)
# fips_libs(libTetWild igl::cgal)

if (NOT FIPS_IMPORT)
    fips_finish()
endif()