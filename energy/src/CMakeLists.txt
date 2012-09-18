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

qt4_wrap_cpp(MOC_SRC ${HDRS})

add_definitions(-DQT_SHARED)
add_library(energy MODULE ${SRC} ${CSRC} ${MOC_SRC})
set_target_properties(energy PROPERTIES PREFIX "")
