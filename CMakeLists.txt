cmake_minimum_required(VERSION 3.7)
project(density VERSION 0.14.2 DESCRIPTION "Superfast compression library" HOMEPAGE_URL "https://github.com/per-mathisen-arm/density" LANGUAGES C)

set(DENSITY_SOURCES
    ${PROJECT_SOURCE_DIR}/src/globals.c
    ${PROJECT_SOURCE_DIR}/src/buffers/buffer.c
    ${PROJECT_SOURCE_DIR}/src/structure/header.c
    ${PROJECT_SOURCE_DIR}/src/algorithms/dictionaries.c
    ${PROJECT_SOURCE_DIR}/src/algorithms/algorithms.c
    ${PROJECT_SOURCE_DIR}/src/algorithms/cheetah/core/cheetah_decode.c
    ${PROJECT_SOURCE_DIR}/src/algorithms/cheetah/core/cheetah_encode.c
    ${PROJECT_SOURCE_DIR}/src/algorithms/chameleon/core/chameleon_decode.c
    ${PROJECT_SOURCE_DIR}/src/algorithms/chameleon/core/chameleon_encode.c
    ${PROJECT_SOURCE_DIR}/src/algorithms/lion/forms/lion_form_model.c
    ${PROJECT_SOURCE_DIR}/src/algorithms/lion/core/lion_decode.c
    ${PROJECT_SOURCE_DIR}/src/algorithms/lion/core/lion_encode.c)

add_library(density STATIC ${DENSITY_SOURCES})
target_compile_options(density PRIVATE -std=c99 -Wall -Ofast -ggdb -Wno-unused-variable -Werror -fno-strict-aliasing -fvisibility=hidden -fPIC ${SANITIZER})
target_link_libraries(density ${SANITIZER})
