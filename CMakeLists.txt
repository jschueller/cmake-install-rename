

cmake_minimum_required (VERSION 2.8.12)

set(CMAKE_BUILD_TYPE "Release" CACHE STRING "Choose the build type")

if(POLICY CMP0025)
  cmake_policy(SET CMP0025 NEW)
endif()

project (hello)

add_executable (hello main.cxx)

install (TARGETS hello DESTINATION bin)
file (MAKE_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/bar)
file (WRITE ${CMAKE_CURRENT_BINARY_DIR}/bar/installed-OTconfig.h "// hello")

set (OPENTURNS_INCLUDE_PATH include)

# install (DIRECTORY bar DESTINATION ${OPENTURNS_INCLUDE_PATH})
install (FILES ${CMAKE_CURRENT_BINARY_DIR}/bar/installed-OTconfig.h
          DESTINATION ${OPENTURNS_INCLUDE_PATH}/bar
          RENAME OTconfig.h
       )
