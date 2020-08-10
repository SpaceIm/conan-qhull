cmake_minimum_required(VERSION 2.8.11)
project(test_package C)

set(CMAKE_VERBOSE_MAKEFILE TRUE)

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

if(QHULL_REENTRANT)
  add_executable(${PROJECT_NAME} test_package_r.c)
else()
  add_executable(${PROJECT_NAME} test_package.c)
endif()
target_link_libraries(${PROJECT_NAME} ${CONAN_LIBS})
