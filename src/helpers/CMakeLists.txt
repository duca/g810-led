add_library(g810-led_helpers
  help.cpp help.h
  utils.cpp utils.h
  )

target_link_libraries(g810-led_helpers g810-led) 

target_include_directories(g810-led_helpers INTERFACE ${CMAKE_CURRENT_SOURCE_DIR})

install(TARGETS g810-led_helpers DESTINATION lib)
install(FILES help.h utils.h DESTINATION include/${CMAKE_PROJECT_NAME})
