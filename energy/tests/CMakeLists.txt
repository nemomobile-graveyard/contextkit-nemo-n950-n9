PROJECT(contextkit_energy_mon)

set(energy_mon_HDRS
  energy_mon.hpp
  )

set(energy_mon_SRC
  energy_mon.cpp
  )

qt4_wrap_cpp(MOC_SRC ${energy_mon_HDRS})

add_definitions(-DQT_SHARED)
add_executable(energy_mon ${energy_mon_SRC} ${MOC_SRC})

TARGET_LINK_LIBRARIES(energy_mon
  ${QT_QTCORE_LIBRARY}
  ${CONTEXTSUBSCRIBER_LIBRARIES}
)

install(TARGETS energy_mon DESTINATION bin)
