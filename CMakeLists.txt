cmake_minimum_required(VERSION 2.8)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake/Modules/")

project(g810-led)

add_subdirectory(src)

install(DIRECTORY sample_effects  DESTINATION share/${CMAKE_PROJECT_NAME})
install(DIRECTORY sample_profiles DESTINATION share/${CMAKE_PROJECT_NAME})
install(DIRECTORY udev            DESTINATION share/${CMAKE_PROJECT_NAME})
install(DIRECTORY systemd         DESTINATION share/${CMAKE_PROJECT_NAME})


