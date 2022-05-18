cmake_minimum_required(VERSION 3.10)

project(threadpool LANGUAGES CXX)

add_definitions(-DTHREADPOOL_LIB=1)

include_directories(../../include)
link_directories(../../lib)
#link_libraries(Threads::Threads)

set(HEADERS ../../include/threadpool/ThreadPool.h)
set(SOURCES ThreadPool.cpp)

SET(CMAKE_CXX_STANDARD 17)

add_library(threadpool SHARED ${HEADERS} ${SOURCES})


set(INSTALL_BIN_DIR "${CMAKE_INSTALL_PREFIX}/bin" CACHE PATH "Installation directory for executables")
set(INSTALL_LIB_DIR "${CMAKE_INSTALL_PREFIX}/lib" CACHE PATH "Installation directory for libraries")
set(INSTALL_INC_DIR "${CMAKE_INSTALL_PREFIX}/include" CACHE PATH "Installation directory for headers")
set(INSTALL_ETC_DIR "${CMAKE_INSTALL_PREFIX}/etc" CACHE PATH "Installation directory for etc")

install(TARGETS threadpool
        RUNTIME DESTINATION "${INSTALL_BIN_DIR}"
        ARCHIVE DESTINATION "${INSTALL_LIB_DIR}"
        LIBRARY DESTINATION "${INSTALL_LIB_DIR}" )

install(FILES ${HEADERS} DESTINATION "${INSTALL_INC_DIR}/threadpool")