# This file is part of CMake-codecov.
#
# Copyright (c)
#   2015-2020 RWTH Aachen University, Federal Republic of Germany
#
# See the LICENSE file in the package base directory for details
#
# Written by Alexander Haase, alexander.haase@rwth-aachen.de
#

set(GENERATED_VALUE 100)
configure_file(${CMAKE_CURRENT_SOURCE_DIR}/gen.h.in ${CMAKE_CURRENT_BINARY_DIR}/gen.h @ONLY)
configure_file(${CMAKE_CURRENT_SOURCE_DIR}/gen.c.in ${CMAKE_CURRENT_BINARY_DIR}/gen.c @ONLY)
add_library(gen SHARED ${CMAKE_CURRENT_BINARY_DIR}/gen.h ${CMAKE_CURRENT_BINARY_DIR}/gen.c)
target_include_directories(gen PUBLIC ${CMAKE_CURRENT_BINARY_DIR})
add_coverage(gen)
