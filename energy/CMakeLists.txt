PROJECT(contextkit_energy)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -DBME_API=11")

set(SRC
  energy.cpp
  )

set(CSRC
  bmeipc.c
  )

set(HDRS
  energy.hpp
  )

set(energy_mon_HDRS
  energy_mon.hpp
  )

set(energy_mon_SRC
  energy_mon.cpp
  )

qt4_wrap_cpp(MOC_SRC ${HDRS})
qt4_wrap_cpp(energy_mon_MOC_SRC ${energy_mon_HDRS})

add_definitions(-DQT_SHARED)
add_library(energy MODULE ${SRC} ${CSRC} ${MOC_SRC})
set_target_properties(energy PROPERTIES PREFIX "")

add_executable(energy_mon ${energy_mon_SRC} ${energy_mon_MOC_SRC})

TARGET_LINK_LIBRARIES(energy_mon
  ${QT_QTGUI_LIBRARY}
  ${QT_QTCORE_LIBRARY}
  ${CONTEXTSUBSCRIBER_LIBRARIES}
)
