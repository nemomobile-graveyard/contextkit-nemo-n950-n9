cmake_minimum_required(VERSION 2.8)

find_package(Qt4 4.7.0 REQUIRED)
find_package(PkgConfig)
include(${QT_USE_FILE})

set(CMAKE_C_FLAGS "${CMAKE_CXX_FLAGS} -W -Wall -Wextra -Werror -g -O2")

#-Wno-psabi is to remove next g++ warning/note:
#the mangling of 'va_list' has changed in GCC 4.4
set(CMAKE_CXX_FLAGS "${CMAKE_C_FLAGS} -Wno-psabi")

pkg_check_modules(CONTEXTSUBSCRIBER contextsubscriber-1.0)

include_directories(
  ${QT_INCLUDE_DIR}
  ${CONTEXTSUBSCRIBER_INCLUDE_DIRS}
)

link_directories(
  ${CONTEXTSUBSCRIBER_LIBRARY_DIRS}
)

add_subdirectory(power)
