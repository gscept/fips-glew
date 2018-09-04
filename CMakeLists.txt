#
# project: fips-glew
#
cmake_minimum_required(VERSION 2.8)

# include the fips main cmake file
get_filename_component(FIPS_ROOT_DIR "../fips" ABSOLUTE)
include("${FIPS_ROOT_DIR}/cmake/fips.cmake")

fips_setup()
fips_project(fips-glew)
fips_begin_lib(glew)
    add_definitions(-DGLEW_STATIC)
    find_package (OpenGL REQUIRED)
    include_directories (${GLEW_DIR}/include)
    fips_src(glew/src NO_RECURSE)
fips_end_lib()
fips_finish()
