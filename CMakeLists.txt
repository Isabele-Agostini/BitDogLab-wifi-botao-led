# == DO NOT EDIT THE FOLLOWING LINES for the Raspberry Pi Pico VS Code Extension to work ==
if(WIN32)
    set(USERHOME $ENV{USERPROFILE})
else()
    set(USERHOME $ENV{HOME})
endif()
set(sdkVersion 1.5.1)
set(toolchainVersion 13_3_Rel1)
set(picotoolVersion 2.1.0)
set(picoVscode ${USERHOME}/.pico-sdk/cmake/pico-vscode.cmake)
if (EXISTS ${picoVscode})
    include(${picoVscode})
endif()
# ====================================================================================
# Generated Cmake Pico project file

cmake_minimum_required(VERSION 3.13)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# == DO NOT EDIT THE FOLLOWING LINES for the Raspberry Pi Pico VS Code Extension to work ==
if(WIN32)
    set(USERHOME $ENV{USERPROFILE})
else()
    set(USERHOME $ENV{HOME})
endif()
set(sdkVersion 1.5.1)
set(toolchainVersion 13_3_Rel1)
set(picotoolVersion 2.1.0)
set(picoVscode ${USERHOME}/.pico-sdk/cmake/pico-vscode.cmake)
if (EXISTS ${picoVscode})
    include(${picoVscode})
endif()
# ====================================================================================
set(PICO_BOARD pico_w CACHE STRING "Board type")

# Pull in Raspberry Pi Pico SDK (must be before project)
include(pico_sdk_import.cmake)

project(controle_botao_led C CXX ASM)

# Initialise the Raspberry Pi Pico SDK
pico_sdk_init()

# Adiciona o executável. Aqui você deve garantir que o arquivo "controle_botao_led.c" existe!
add_executable(controle_botao_led controle_botao_led.c)

pico_set_program_name(controle_botao_led "controle_botao_led")
pico_set_program_version(controle_botao_led "0.1")

# Habilita saída USB (desativa UART)
pico_enable_stdio_uart(controle_botao_led 0)
pico_enable_stdio_usb(controle_botao_led 1)

# Bibliotecas padrão
target_link_libraries(controle_botao_led pico_stdlib)

# Diretórios de include
target_include_directories(controle_botao_led PRIVATE ${CMAKE_CURRENT_LIST_DIR})

# Bibliotecas extras para Wi-Fi com threading seguro
target_link_libraries(controle_botao_led pico_cyw43_arch_lwip_threadsafe_background)

# Geração dos binários, UF2 etc
pico_add_extra_outputs(controle_botao_led)
