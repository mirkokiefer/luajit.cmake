
cmake_minimum_required(VERSION 2.8)
include(ExternalProject)

project(luajit)

ExternalProject_Add(project_luajit
  URL http://luajit.org/download/LuaJIT-2.0.1.tar.gz
  PREFIX ${CMAKE_CURRENT_BINARY_DIR}/luajit
  INSTALL_DIR ${CMAKE_INSTALL_PREFIX}
  CONFIGURE_COMMAND ""
  BUILD_COMMAND make
  INSTALL_COMMAND make install PREFIX=${CMAKE_INSTALL_PREFIX}
  BUILD_IN_SOURCE 1
)