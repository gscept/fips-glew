#
# project: fips-glew
#
cmake_minimum_required(VERSION 3.21)

if (NOT FIPS_IMPORT)
# include the fips main cmake file
get_filename_component(FIPS_ROOT_DIR "../fips" ABSOLUTE)
include("${FIPS_ROOT_DIR}/cmake/fips.cmake")

    project(fips-glew)
fips_setup()
endif()

fips_begin_lib(glew)
    add_definitions(-DGLEW_STATIC)
    find_package (OpenGL REQUIRED)
    target_include_directories (glew PRIVATE ${GLEW_DIR}/include)
    fips_src(glew/src NO_RECURSE)
fips_end_lib()