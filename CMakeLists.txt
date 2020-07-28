cmake_minimum_required(VERSION 3.14)
project(coro)

add_compile_definitions(HAVE_CORO)

set(SOURCE_FILES coro.c)
set(HEADER_FILES php_coro.h)

if (DEFINED PHP_CONFIG_DIR)
    set(PHP_CONFIG_DIR "${PHP_CONFIG_DIR}/")
else()
    set(PHP_CONFIG_DIR "")
endif()

execute_process (
        COMMAND ${PHP_CONFIG_DIR}php-config --include-dir
        OUTPUT_VARIABLE PHP_INCLUDE_DIR
        OUTPUT_STRIP_TRAILING_WHITESPACE
)

execute_process(
        COMMAND ${PHP_CONFIG_DIR}php-config --libs
        OUTPUT_VARIABLE PHP_LIBS
        OUTPUT_STRIP_TRAILING_WHITESPACE
)

execute_process(
        COMMAND ${PHP_CONFIG_DIR}php-config --ldflags
        OUTPUT_VARIABLE PHP_LDFLAGS
        OUTPUT_STRIP_TRAILING_WHITESPACE
)

message("Using source directory: ${PHP_SOURCE}")

include_directories(${PHP_SOURCE})
include_directories(${PHP_SOURCE}/main)
include_directories(${PHP_SOURCE}/Zend)
include_directories(${PHP_SOURCE}/TSRM)
include_directories(${PROJECT_SOURCE_DIR})

add_library(___ EXCLUDE_FROM_ALL ${SOURCE_FILES})

target_link_libraries(coro-ext coro)