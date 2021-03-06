# Copyright (C) 2017, Verizon, Inc. All rights reserved.
# ThingSpace SDK Components

set( TARGETS ts_sdk_components )

file( GLOB SOURCES
    "*.c"
    "service/*.c"
    "transport/*.c"
    "security/*.c"
    "controller/at_interpreter/*.c"
    "controller/*.c" )

add_library( ts_sdk_components OBJECT ${SOURCES} )

target_include_directories( ts_sdk_components PRIVATE
    ${CMAKE_SOURCE_DIR}/sdk/include
    ${CMAKE_SOURCE_DIR}/sdk_dependencies/cJSON
    ${CMAKE_SOURCE_DIR}/sdk_dependencies/tinycbor/src
    ${CMAKE_SOURCE_DIR}/sdk_dependencies/mbedtls/include
    ${CMAKE_SOURCE_DIR}/sdk_dependencies/paho.mqtt.embedded-c/MQTTPacket/src
    ${CMAKE_SOURCE_DIR}/sdk_dependencies/paho.mqtt.embedded-c/MQTTClient-C/src
    ${CMAKE_SOURCE_DIR}/sdk_dependencies/mocana/src )

# note - mocana specific defines
target_compile_definitions( ts_sdk_components PRIVATE
    __RTOS_TSSDK__
    __ENABLE_MOCANA_SSL_CLIENT__
    __ENABLE_MOCANA_SSL_ASYNC_CLIENT_API__
    __ENABLE_MOCANA_SSL_DUAL_MODE_API__ )
