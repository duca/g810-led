cmake_minimum_required(VERSION 2.8)

project(g810-led)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake/Modules/")
include(FindHIDAPI)
include(FindLibUSB)

add_subdirectory(src)

set(BASE_DIRECTORY "/etc")
if (NOT CMAKE_INSTALL_PREFIX STREQUAL "/usr" AND
    NOT CMAKE_INSTALL_PREFIX STREQUAL "/usr/local")
  set(BASE_DIRECTORY "etc")
endif()

install(DIRECTORY sample_effects  DESTINATION ${BASE_DIRECTORY}/${CMAKE_PROJECT_NAME})
install(DIRECTORY sample_profiles DESTINATION ${BASE_DIRECTORY}/${CMAKE_PROJECT_NAME})
install(DIRECTORY udev/           DESTINATION ${BASE_DIRECTORY}/udev/rules.d/)
install(DIRECTORY systemd/        DESTINATION ${BASE_DIRECTORY}/systemd/user)  
  
include(Packer)


