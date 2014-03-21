cmake_minimum_required(VERSION 2.8)
project(ptex)

set(INSTALL_INCLUDE_DIR "include" CACHE PATH "Includes install path")
set(INSTALL_LIB_DIR "lib" CACHE PATH "Library install path")
set(INSTALL_BIN_DIR "bin" CACHE PATH "Binary install path")

set(PTEX_BUILD_UTILS ON CACHE BOOL "Build ptxinfo")
set(PTEX_ENABLE_TESTS ON CACHE BOOL "Enable tests")
set(PTEX_BUILD_DOCS ON CACHE BOOL "Build documentation")

# enable testing for the project
include(CTest)
if (PTEX_ENABLE_TESTS)
  enable_testing()
endif()

include(FindZLIB)
include(FindThreads)

include_directories(ptex)
include_directories(${ZLIB_INCLUDE_DIR})

add_subdirectory(ptex)
if (PTEX_BUILD_UTILS)
  add_subdirectory(utils)
endif()

if(PTEX_ENABLE_TESTS)
  add_subdirectory(tests)
endif()
if(PTEX_BUILD_DOCS)
  add_subdirectory(doc)
endif()
