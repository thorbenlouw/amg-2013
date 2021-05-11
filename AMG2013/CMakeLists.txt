# Adapted from the Hypre CMakeLists.txt at  https://github.com/hypre-space/hypre
# Copyright 1998-2019 Lawrence Livermore National Security, LLC and other
# HYPRE Project Developers. See the top-level COPYRIGHT file for details.
#
# SPDX-License-Identifier: (Apache-2.0 OR MIT)

cmake_minimum_required (VERSION 3.13...3.16)

if(${CMAKE_VERSION} VERSION_LESS 3.16)
    cmake_policy(VERSION ${CMAKE_MAJOR_VERSION}.${CMAKE_MINOR_VERSION})
else()
    cmake_policy(VERSION 3.16)
endif()

project (amg
        VERSION 2013
        LANGUAGES C CXX)

if (${amg_SOURCE_DIR} STREQUAL ${amg_BINARY_DIR})
    message(FATAL_ERROR "In-place build not allowed! Please use a separate build directory. See the Users Manual or INSTALL file for details.")
endif ()


if (NOT CMAKE_BUILD_TYPE AND NOT CMAKE_CONFIGURATION_TYPES)
    set (CMAKE_BUILD_TYPE "${HYPRE_BUILD_TYPE}" CACHE INTERNAL "" FORCE)
    # Set the possible values of build type for cmake-gui
    set_property(CACHE CMAKE_BUILD_TYPE PROPERTY STRINGS
            "Debug" "Release" "MinSizeRel" "RelWithDebInfo")
endif ()


find_package(MPI REQUIRED)
find_package(OpenMP REQUIRED)
include_directories(${MPI_INCLUDE_PATH})
include_directories(/usr/local/opt/libomp/include)

set(INCLUDE_CFLAGS -O2 -DTIMER_USE_MPI -DHYPRE_USING_OPENMP -DHYPRE_LONG_LONG -DHYPRE_NO_GLOBAL_PARTITION )
set(INCLUDE_LFLAGS -lm -Xpreprocessor -fopenmp)
add_compile_options(${INCLUDE_CFLAGS})
add_link_options(${INCLUDE_LFLAGS})
add_subdirectory(utilities)
add_subdirectory(IJ_mv)
add_subdirectory(krylov)
add_subdirectory(parcsr_ls)
add_subdirectory(parcsr_mv)
add_subdirectory(seq_mv)
add_subdirectory(sstruct_mv)
add_subdirectory(struct_mv)
add_subdirectory(test)

