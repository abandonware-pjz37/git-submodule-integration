cmake_minimum_required(VERSION 3.0)

include("cmake/HunterGate.cmake")
HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.21.17.tar.gz"
    SHA1 "c414960e1218d6e3d97ad095de59e106b8973c3e"
    LOCAL
)

project(foo)

hunter_add_package(fruits)
find_package(fruits CONFIG REQUIRED)

add_executable(foo foo.cpp)
target_link_libraries(foo PUBLIC fruits::fruits_rosaceae)

enable_testing()
add_test(NAME foo COMMAND foo)
