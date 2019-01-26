macro(build_test target)
  set(sources ${ARGN})
  add_executable(${target} ${sources})
  format_output_name(${target} ${target})
  target_include_directories(${target} PRIVATE
    ${SimTool2_SOURCE_DIR}/plot/include
    ${CMAKE_CURRENT_SOURCE_DIR}/include
    )
  target_link_libraries(${target} plot)
  set_target_properties(${target} PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${SimTool2_BINARY_DIR})
endmacro()

### Tests ####################################################################

build_test(test_plot include/MySignal.h src/MySignal.cpp src/test_plot.cpp)
