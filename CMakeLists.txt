PROJECT(pluLink3D)

# min cmake version
CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

SET(CMAKE_CXX_FLAGS "-std=c++11")

# default to debug
SET(CMAKE_BUILD_TYPE "Debug" CACHE STRING "Debug or Release")

# configure debug / release flags
IF (CMAKE_BUILD_TYPE MATCHES Debug)
  # debug define
  ADD_DEFINITIONS(-DDEBUG=1)
  # Add -g for unix
  IF(UNIX)
    SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g")
  ENDIF(UNIX)
ELSEIF (CMAKE_BUILD_TYPE MATCHES Release)
  # Add unix optimization flag
  IF(UNIX)
    SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS}  -O2")
  ENDIF(UNIX)
ENDIF (CMAKE_BUILD_TYPE MATCHES Debug)

ADD_EXECUTABLE(pluLink3D ${CMAKE_CURRENT_SOURCE_DIR}/plu_link3Dt.cpp)