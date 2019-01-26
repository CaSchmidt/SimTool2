macro(build_example target)
  set(sources ${ARGN})
  add_library(${target} SHARED ${sources})
  format_output_name(${target} ${target})
  target_include_directories(${target} PRIVATE
    ${SimTool2_SOURCE_DIR}/core/include
    )
  target_link_libraries(${target} core)
  set_target_properties(${target} PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${SimTool2_BINARY_DIR})
endmacro()

### Examples #################################################################

build_example(signals signals/src/main.cpp)
build_example(test test/src/main.cpp)
