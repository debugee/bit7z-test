cmake_minimum_required(VERSION 3.20)

set(CMAKE_TOOLCHAIN_FILE "$ENV{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake")

set(VCPKG_INSTALL_OPTIONS --overlay-ports=${CMAKE_CURRENT_SOURCE_DIR}/overlay)

set(VCPKG_TARGET_TRIPLET x64-osx-dynamic)

project(test VERSION 1.0)

set(CMAKE_CXX_STANDARD 17)

set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_executable(test test.cpp)

find_package(unofficial-bit7z CONFIG REQUIRED)

target_link_libraries(test PRIVATE unofficial::bit7z::bit7z64)