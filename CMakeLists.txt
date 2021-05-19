cmake_minimum_required(VERSION 3.12)

set(PROJECT fatfs_reader)

include(pico_sdk_import.cmake)

project(${PROJECT})

pico_sdk_init()

add_executable(${PROJECT}
    src/main.c
    src/msc_disk.c
    src/usb_descriptors.c
)

target_include_directories(${PROJECT} PRIVATE src)
target_link_libraries(${PROJECT} PRIVATE
  pico_stdlib
  pico_unique_id
  tinyusb_device
  tinyusb_board
  pico_bootsel_via_double_reset
  pico_fix_rp2040_usb_device_enumeration
)

pico_add_extra_outputs(${PROJECT})