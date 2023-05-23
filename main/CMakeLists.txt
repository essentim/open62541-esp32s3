
idf_component_register(SRCS "main.c"
                       PRIV_INCLUDE_DIRS ${IDF_PATH}/components/freertos/FreeRTOS-Kernel/include/freertos 
                       REQUIRES open62541 nvs_flash esp_adc esp_event esp_wifi spi_flash driver)

# Build static library, do not build test executables
option(BUILD_SHARED_LIBS OFF)
option(BUILD_TESTING OFF)

# ESP32 is little endian
#add_definitions(-DUA_ENABLE_AMALGAMATION -DUA_ARCHITECTURE_FREERTOSLWIP -DUA_ARCHITECTURE_FREERTOSLWIP_POSIX_CLOCK)
#add_definitions(-Wno-ignored-qualifiers)

# Unfortunately the library performs install and export. Would
# have been nice if devs made that an option like BUILD_SHARED_LIBS
# and BUILD_TESTING. Override install() and export() to do nothing
# instead.
function(install)
endfunction()

function(export)
endfunction()
