add_library(g810-led
  Keyboard.cpp
  Keyboard.h
  )

target_include_directories(g810-led
  INTERFACE
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
  )

if (LibUSB_FOUND)
  set_target_properties(
    PROPERTIES
    COMPILE_FLAGS
    libusb=y
    )
  target_link_libraries(g810-led
    ${usb_LIBRARY}    
    ) 
  target_compile_definitions(g810-led PUBLIC libusb=1)
elseif(HIDAPI_FOUND)
  set_target_properties (
    PROPERTIES
    COMPILE_FLAGS
    hidapi=y
    )
  target_link_libraries(g810-led
    ${HIDAPI_LIBRARIES}
    ) 
#  target_compile_definitions(g810-led PUBLIC hidapi=1)  
endif()

install(TARGETS g810-led DESTINATION lib)
install(FILES Keyboard.h DESTINATION include/${CMAKE_PROJECT_NAME})
