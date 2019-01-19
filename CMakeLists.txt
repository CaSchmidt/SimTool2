cmake_minimum_required(VERSION 3.2 FATAL_ERROR)

project(SimTool2-dev)

add_subdirectory(SimTool2)

set_target_properties(core PROPERTIES
  RUNTIME_OUTPUT_DIRECTORY ${SimTool2_BINARY_DIR}
  )
