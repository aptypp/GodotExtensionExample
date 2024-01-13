cmake_minimum_required(VERSION 3.28.1)
project(my_extension LANGUAGES CXX)

link_directories(${my_extension}
        ${PROJECT_SOURCE_DIR}/godot-cpp/build/bin)

FILE(GLOB HEADERS ${PROJECT_SOURCE_DIR}/include/*)
FILE(GLOB SRC ${PROJECT_SOURCE_DIR}/src/*)

add_library(my_extension_lib SHARED ${SRC} ${HEADERS})

target_link_libraries(my_extension_lib PRIVATE libgodot-cpp.linux.release.64.a)

target_include_directories(my_extension_lib PUBLIC include godot-cpp/include godot-cpp/build/gen/include godot-cpp/gdextension)

set_target_properties(my_extension_lib PROPERTIES
         LIBRARY_OUTPUT_DIRECTORY ../bin)