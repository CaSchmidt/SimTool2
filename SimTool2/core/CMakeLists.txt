set(core_HEADERS
  include/internal/SimDataSeriesPriv.h
  include/SimCore/ISimLogger.h
  include/SimCore/ISimValue.h
  include/SimCore/ISimVariableXfer.h
  include/SimCore/Sim.h
  include/SimCore/SimConfig.h
  include/SimCore/SimContext.h
  include/SimCore/SimControl.h
  include/SimCore/SimDataLogger.h
  include/SimCore/SimDataSeries.h
  include/SimCore/SimDataTypeId.h
  include/SimCore/SimDb.h
  include/SimCore/SimDbStore.h
  include/SimCore/SimEnvironment.h
  include/SimCore/SimModule.h
  include/SimCore/SimModuleRunner.h
  include/SimCore/SimModulesModel.h
  include/SimCore/SimSimulator.h
  include/SimCore/SimUtil.h
  include/SimCore/SimValuesModel.h
  include/SimCore/SimVariable.h
  include/SimCore/SimVariablesModel.h
  include/SimCore/sim_mod.h
  include/SimCore/simcore_config.h
  )

set(core_SOURCES
  src/ISimValue.cpp
  src/ISimVariableXfer.cpp
  src/SimContext.cpp
  src/SimControl.cpp
  src/SimDataLogger.cpp
  src/SimDataSeries.cpp
  src/SimDb.cpp
  src/SimEnvironment.cpp
  src/SimModule.cpp
  src/SimModuleRunner.cpp
  src/SimModulesModel.cpp
  src/SimSimulator.cpp
  src/SimUtil.cpp
  src/SimValuesModel.cpp
  src/SimVariable.cpp
  src/SimVariablesModel.cpp
  src/sim_mod.cpp
  )

add_library(core SHARED
  ${core_HEADERS} ${core_SOURCES}
  )

target_link_libraries(core Qt5::Core)

format_output_name(core "SimCore")

target_compile_definitions(core PRIVATE SIM_BUILD_CORE_LIB)
target_include_directories(core PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/include)

install(TARGETS core
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
  RUNTIME DESTINATION bin
  )
