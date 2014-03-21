if (WIN32)
  add_definitions ( /DPTEX_EXPORTS )
endif (WIN32)

set(SRCS
    PtexCache.cpp
    PtexFilters.cpp
    PtexHalf.cpp
    PtexReader.cpp
    PtexSeparableFilter.cpp
    PtexSeparableKernel.cpp
    PtexTriangleFilter.cpp
    PtexTriangleKernel.cpp
    PtexUtils.cpp
    PtexWriter.cpp)

add_library(Ptex ${SRCS})
target_link_libraries(Ptex ${CMAKE_THREAD_LIBS_INIT} ${ZLIB_LIBRARIES})
install(TARGETS Ptex DESTINATION ${INSTALL_LIB_DIR})
install(FILES Ptexture.h PtexHalf.h PtexInt.h PtexUtils.h
  DESTINATION ${INSTALL_INCLUDE_DIR})
