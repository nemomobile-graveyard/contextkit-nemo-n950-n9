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

set(energy_test_HDRS
  energy_test.hpp
  )

set(energy_test_SRC
  energy_test.cpp
  )

qt4_wrap_cpp(MOC_SRC ${HDRS})
qt4_wrap_cpp(energy_test_MOC_SRC ${energy_test_HDRS})

add_definitions(-DQT_SHARED)
add_library(energy MODULE ${SRC} ${CSRC} ${MOC_SRC})
set_target_properties(energy PROPERTIES PREFIX "")

add_executable(energy_test ${energy_test_SRC} ${energy_test_MOC_SRC})

TARGET_LINK_LIBRARIES(energy_test
  ${QT_QTGUI_LIBRARY}
  ${QT_QTCORE_LIBRARY}
  ${CONTEXTSUBSCRIBER_LIBRARIES}
)
