
cmake_minimum_required(VERSION 2.8)
include(ExternalProject)

project(luajit)

ExternalProject_Add(project_luajit
  URL http://luajit.org/download/LuaJIT-2.0.1.tar.gz
  PREFIX ${CMAKE_CURRENT_BINARY_DIR}/luajit
  CONFIGURE_COMMAND ""
  BUILD_COMMAND make
  INSTALL_COMMAND make install PREFIX=${CMAKE_CURRENT_BINARY_DIR}/luajit
  BUILD_IN_SOURCE 1
)

ExternalProject_Get_Property(project_luajit install_dir)

install(DIRECTORY ${install_dir}/bin/ DESTINATION bin)
install(DIRECTORY ${install_dir}/lib/ DESTINATION lib)
install(DIRECTORY ${install_dir}/include/ DESTINATION include)