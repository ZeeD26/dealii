## ---------------------------------------------------------------------
##
## Copyright (C) 2012 - 2016 by the deal.II authors
##
## This file is part of the deal.II library.
##
## The deal.II library is free software; you can use it, redistribute
## it, and/or modify it under the terms of the GNU Lesser General
## Public License as published by the Free Software Foundation; either
## version 2.1 of the License, or (at your option) any later version.
## The full text of the license can be found in the file LICENSE at
## the top level of the deal.II distribution.
##
## ---------------------------------------------------------------------

IF(DEAL_II_COMPONENT_EXAMPLES)
  MESSAGE(STATUS "Setting up examples")

  INSTALL(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/
    DESTINATION ${DEAL_II_EXAMPLES_RELDIR}
    COMPONENT examples
    FILES_MATCHING
    #
    # Exclude folder structures: doc, doxygen, CMakeFiles,...
    #
    PATTERN "CMakeFiles*" EXCLUDE
    PATTERN "doc*" EXCLUDE
    #
    # Glob Includes:
    #
    PATTERN "*.cc"
    PATTERN "*.prm"
    PATTERN "*.inp"
    PATTERN "step*/CMakeLists.txt"
    PATTERN "doxygen/CMakeLists.txt"
    #
    # Special files:
    #
    PATTERN "output.reference.dat"        # step-39
    PATTERN "postprocess.pl"              # step-39
    PATTERN "obstacle.pbm"                # step-42
    PATTERN "untitled.geo"                # step-49
    PATTERN "untitled.msh"                # step-49
    PATTERN "topography.txt.gz"           # step-53
    PATTERN "input/initial_mesh_3d.vtk"   # step-54
    PATTERN "DTMB-5415_bulbous_bow.iges"  # step-54
    )

  MESSAGE(STATUS "Setting up examples - Done")
ENDIF()

#
# Add a dummy target to make files known to IDEs like qtcreator
#

FILE(GLOB _misc
  ${CMAKE_CURRENT_SOURCE_DIR}/step-*/*.cc
  ${CMAKE_CURRENT_SOURCE_DIR}/step-*/*.h
)
ADD_CUSTOM_TARGET(dummy_examples_files
  SOURCES ${_misc}
  )
