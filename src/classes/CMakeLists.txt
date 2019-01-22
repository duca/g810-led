add_library(g810-led
  Keyboard.cpp
  Keyboard.h
  )

if (LibUSB_FOUND)
  target_link_libraries(g810-led
    usb_LIBRARY    
    ) 
  target_compile_definitions(g810-led PUBLIC libusb=1)
elseif(HIDAPI_FOUND)
  target_link_libraries(g810-led
    HIDAPI_LIBRARIES
    ) 
#  target_compile_definitions(g810-led PUBLIC hidapi=1)  
endif()

install(TARGETS g810-led DESTINATION lib)
install(FILES Keyboard.h DESTINATION include/${CMAKE_PROJECT_NAME})
