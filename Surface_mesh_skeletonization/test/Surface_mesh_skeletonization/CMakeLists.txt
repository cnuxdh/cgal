# Created by the script cgal_create_cmake_script
# This is the CMake script for compiling a CGAL application.


cmake_minimum_required(VERSION 3.1...3.15)
project( Surface_mesh_skeletonization_Tests )



find_package(CGAL QUIET)

if ( CGAL_FOUND )

  find_package(Eigen3 3.2.0) #(requires 3.2.0 or greater)

  if(EIGEN3_FOUND)
    create_single_source_cgal_program( "MCF_Skeleton_test.cpp" )
    CGAL_target_use_Eigen(MCF_Skeleton_test)
    create_single_source_cgal_program( "skeleton_connectivity_test.cpp" )
    CGAL_target_use_Eigen(skeleton_connectivity_test)
  else()
    message(STATUS "These tests require the Eigen library (3.2 or greater), and will not be compiled.")
  endif()
else()

    message(STATUS "This program requires the CGAL library, and will not be compiled.")

endif()

