cmake_minimum_required(VERSION 3.1)
project(main)

include_directories(
  ${CMAKE_SYSROOT}/usr/include/c++/8
  ${CMAKE_SYSROOT}/usr/include/${target}/c++/8
)

link_directories(
  ${CMAKE_SYSROOT}/usr/lib/gcc/${target}/8
)

add_executable(${PROJECT_NAME} main.cpp)
