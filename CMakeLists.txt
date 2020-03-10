

cmake_minimum_required (VERSION 2.8.12)

set(CMAKE_BUILD_TYPE "Release" CACHE STRING "Choose the build type")

if(POLICY CMP0025)
  cmake_policy(SET CMP0025 NEW)
endif()

project (hello)

add_executable (hello main.cxx)

install (TARGETS hello DESTINATION bin)
install (FILES hello.hxx DESTINATION include RENAME hello2.hxx)

