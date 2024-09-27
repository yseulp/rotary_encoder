cmake_minimum_required(VERSION 3.13)
include(pico-sdk/pico_sdk_init.cmake)

project(display_project)

# Initialisiere das Pico SDK
pico_sdk_init()

# Füge den ausführbaren Code hinzu
add_executable(ili9341_display
    main.c
    lib/ili9341/ili9341.c
)

# Verlinke die Bibliotheken (pico_stdlib und hardware_spi für das Display)
target_link_libraries(ili9341_display
    pico_stdlib
    hardware_spi
    hardware_dma
)

# Verlinke die Header-Dateien für die Bibliotheken
target_include_directories(ili9341_display PRIVATE
    ${CMAKE_CURRENT_LIST_DIR}
    ${CMAKE_CURRENT_LIST_DIR}/path/to/board_config
)

# Füge die Ausgabeformate hinzu (z.B. UF2-Datei)
pico_add_extra_outputs(ili9341_display)
