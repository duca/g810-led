add_subdirectory(classes)
add_subdirectory(helpers)

add_executable(g810-led-bin
  main.cpp
  )

target_link_libraries(g810-led-bin
  g810-led
  g810-led_helpers
  )

install(TARGETS g810-led-bin DESTINATION bin)

