cmake_minimum_required(VERSION 3.2 FATAL_ERROR)

### Project ##################################################################

project(SimTool2)

# Build Tests?
option(ENABLE_TESTS "Enable tests" OFF)

### Modules ##################################################################

list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)
include(FormatOutputName)

### Dependencies #############################################################

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOUIC_SEARCH_PATHS ${CMAKE_CURRENT_SOURCE_DIR}/forms)
find_package(Qt5Widgets 5.9 REQUIRED)
find_package(Qt5Charts 5.9 REQUIRED)

add_subdirectory(../csQt/csQt
  ${CMAKE_CURRENT_BINARY_DIR}/csQt
  )

set_target_properties(csQt PROPERTIES
  RUNTIME_OUTPUT_DIRECTORY ${SimTool2_BINARY_DIR}
  )

### Targets ##################################################################

add_definitions(-DQT_NO_CAST_FROM_ASCII -DQT_NO_CAST_TO_ASCII)

add_subdirectory(core)
add_subdirectory(plot)
add_subdirectory(gui)
add_subdirectory(examples)

if(ENABLE_TESTS)
  add_subdirectory(tests)
endif()
