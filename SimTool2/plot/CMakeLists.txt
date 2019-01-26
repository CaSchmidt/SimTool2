set(plot_HEADERS
  include/internal/AxisLabel.h
  include/internal/Draw.h
  include/internal/IAxisElement.h
  include/internal/IPlotElement.h
  include/internal/IPlotImplementation.h
  include/internal/ISeriesControl.h
  include/internal/ITitleElement.h
  include/internal/IViewportControl.h
  include/internal/IXAxisControl.h
  include/internal/Layout.h
  include/internal/Mapping.h
  include/internal/PanAndZoom.h
  include/internal/Scale.h
  include/internal/Scope.h
  include/internal/ScopeRow.h
  include/internal/Series.h
  include/internal/SeriesStore.h
  include/internal/SinglePlotImpl.h
  include/internal/XAxis.h
  include/internal/XTitle.h
  include/internal/YAxis.h
  include/internal/YTitle.h
  include/SimPlot/ISimPlotSeriesData.h
  include/SimPlot/SimPlot.h
  include/SimPlot/SimPlotRange.h
  include/SimPlot/SimPlotSeriesHandle.h
  include/SimPlot/SimPlotTheme.h
  include/SimPlot/SimPlotWidget.h
  include/SimPlot/simplot_config.h
  )

set(plot_SOURCES
  src/AxisLabel.cpp
  src/Draw.cpp
  src/IAxisElement.cpp
  src/IPlotElement.cpp
  src/IPlotImplementation.cpp
  src/ISeriesControl.cpp
  src/ISimPlotSeriesData.cpp
  src/ITitleElement.cpp
  src/IViewportControl.cpp
  src/IXAxisControl.cpp
  src/Mapping.cpp
  src/PanAndZoom.cpp
  src/Scale.cpp
  src/Scope.cpp
  src/ScopeRow.cpp
  src/Series.cpp
  src/SeriesStore.cpp
  src/SimPlotRange.cpp
  src/SimPlotSeriesHandle.cpp
  src/SimPlotTheme.cpp
  src/SimPlotWidget.cpp
  src/SinglePlotImpl.cpp
  src/XAxis.cpp
  src/XTitle.cpp
  src/YAxis.cpp
  src/YTitle.cpp
  )

add_library(plot SHARED
  ${plot_HEADERS} ${plot_SOURCES}
  )

target_link_libraries(plot Qt5::Widgets)

format_output_name(plot "SimPlot")

set_target_properties(plot PROPERTIES
  RUNTIME_OUTPUT_DIRECTORY ${SimTool2_BINARY_DIR}
  )

target_compile_definitions(plot PRIVATE SIM_BUILD_PLOT_LIB)
target_include_directories(plot PRIVATE ${SimTool2_SOURCE_DIR}/plot/include)

install(TARGETS plot
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
  RUNTIME DESTINATION bin
  )
