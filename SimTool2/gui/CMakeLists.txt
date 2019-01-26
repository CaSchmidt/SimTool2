set(CMAKE_AUTOUIC_SEARCH_PATHS ${CMAKE_CURRENT_SOURCE_DIR}/forms)

set(gui_FORMS
  forms/wmainwindow.ui
  forms/wmoduleeditor.ui
  forms/wmodules.ui
  forms/wplotwindow.ui
  forms/wvalueswindow.ui
  forms/wvariableeditor.ui
  forms/wvariables.ui
  )

set(gui_HEADERS
  include/config.h
  include/datalogsmodel.h
  include/global.h
  include/valuedelegate.h
  include/wlogdepthspin.h
  include/wlogger.h
  include/wmainwindow.h
  include/wmoduleeditor.h
  include/wmodules.h
  include/wplotwindow.h
  include/wsimconfigbar.h
  include/wvalueswindow.h
  include/wvariableeditor.h
  include/wvariables.h
  )

set(gui_SOURCES
  src/config.cpp
  src/datalogsmodel.cpp
  src/global.cpp
  src/main.cpp
  src/valuedelegate.cpp
  src/wlogdepthspin.cpp
  src/wlogger.cpp
  src/wmainwindow.cpp
  src/wmoduleeditor.cpp
  src/wmodules.cpp
  src/wplotwindow.cpp
  src/wsimconfigbar.cpp
  src/wvalueswindow.cpp
  src/wvariableeditor.cpp
  src/wvariables.cpp
  )

add_executable(gui
  ${gui_HEADERS} ${gui_SOURCES}
  resources/resources.qrc
  )

target_link_libraries(gui core csQt Qt5::Widgets Qt5::Charts)

format_output_name(gui "SimTool2")

if(WIN32)
  set_target_properties(gui PROPERTIES WIN32_EXECUTABLE ON)
endif()

set_target_properties(gui PROPERTIES
  RUNTIME_OUTPUT_DIRECTORY ${SimTool2_BINARY_DIR}
  )

target_include_directories(gui PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/include)
target_include_directories(gui PRIVATE ${SimTool2_SOURCE_DIR}/core/include)
target_include_directories(gui PRIVATE ${csQt_SOURCE_DIR}/include)

install(TARGETS gui
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
  RUNTIME DESTINATION bin
  )
