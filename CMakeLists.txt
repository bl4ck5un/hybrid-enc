cmake_minimum_required(VERSION 3.0)
set(CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake;${CMAKE_MODULE_PATH}")

project(hybrid-enc)

find_package(MbedTLS REQUIRED)

add_executable(hkeygen hkeygen.cpp hybrid_cipher.cpp base64.cpp hexdump.c)
add_executable(henc henc.cpp hybrid_cipher.cpp base64.cpp hexdump.c)
add_executable(hdec hdec.cpp hybrid_cipher.cpp base64.cpp hexdump.c)

target_compile_features(hkeygen PRIVATE cxx_range_for)
target_compile_features(henc PRIVATE cxx_range_for)
target_compile_features(hdec PRIVATE cxx_range_for)

target_link_libraries(hkeygen -lmbedtls -lmbedx509 -lmbedcrypto)
target_link_libraries(henc -lmbedtls -lmbedx509 -lmbedcrypto)
target_link_libraries(hdec -lmbedtls -lmbedx509 -lmbedcrypto)
