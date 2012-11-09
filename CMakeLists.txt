project(ezybackup)

cmake_minimum_required (VERSION 2.8.0 FATAL_ERROR)

# find necessary libs
find_package (Qt4 4.8 COMPONENTS QtCore QtGui QtOpenGL QtXml QtSvg QtNetwork REQUIRED)

if (UNIX AND NOT APPLE AND NOT MINGW)
  set (LINUX 1)
endif (UNIX AND NOT APPLE AND NOT MINGW)

if (MINGW)
  set (WIN32 1)
  
  # Cmake adds -rdynamic to compiler flags.
  # As mingw doesn't know rdynamic, we want to remove this.
  string (REPLACE "-rdynamic" "" CMAKE_SHARED_LIBRARY_LINK_CXX_FLAGS ${CMAKE_SHARED_LIBRARY_LINK_CXX_FLAGS})
endif (MINGW)


include(${QT_USE_FILE})

# set CMAKE_BUILD_TYPE
if (CMAKE_BUILD_TYPE MATCHES Debug)
  set (CMAKE_BUILD_TYPE Debug)
else (CMAKE_BUILD_TYPE MATCHES Debug)
  set (CMAKE_BUILD_TYPE Release)
endif (CMAKE_BUILD_TYPE MATCHES Debug)

# set CXX_FLAGS
set (CMAKE_CXX_FLAGS_RELEASE "-std=c++0x")
set (CMAKE_CXX_FLAGS_DEBUG "-g -Wall -std=c++0x")

add_subdirectory (source)
