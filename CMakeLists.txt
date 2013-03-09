
cmake_minimum_required(VERSION 2.8)
include(ExternalProject)

project(luajit)

set (luajit_version $ENV{LUAJIT_VERSION})

if ("${lua_version}" STREQUAL "")
  set(luajit_version 2.0.1)
endif()

ExternalProject_Add(project_luajit
  URL http://luajit.org/download/LuaJIT-${luajit_version}.tar.gz
  PREFIX ${CMAKE_CURRENT_BINARY_DIR}/luajit-${luajit_version}
  CONFIGURE_COMMAND ""
  BUILD_COMMAND make
  INSTALL_COMMAND make install PREFIX=${CMAKE_CURRENT_BINARY_DIR}/luajit-${luajit_version}
  BUILD_IN_SOURCE 1
)

ExternalProject_Get_Property(project_luajit install_dir)

install(DIRECTORY ${install_dir}/bin/ DESTINATION bin)
install(DIRECTORY ${install_dir}/lib/ DESTINATION lib)
install(DIRECTORY ${install_dir}/include/ DESTINATION include)