cmake_minimum_required(VERSION 2.6)
project(pugixml-sample CXX)


set(PROJECT_EXEC "main")


message(STATUS "Build type: ${CMAKE_BUILD_TYPE}.")

set(CMAKE_CXX_FLAGS_DEBUG "-O0 -g -ggdb")
set(CMAKE_CXX_FLAGS_RELEASE "-O3")
set(CMAKE_CXX_FLAGS "-std=c++11 -Wall -Wextra -Werror -pedantic")


set(LIBS_DIR "${CMAKE_CURRENT_SOURCE_DIR}/lib")

# pugixml.
add_subdirectory("${LIBS_DIR}/pugixml/scripts" "lib/pugixml")
include_directories("${LIBS_DIR}/pugixml/src")

message(STATUS "pugixml include dir: ${PUGIXML_INCLUDE_DIR}")


set(SRC_DIR "${CMAKE_CURRENT_SOURCE_DIR}/src")
file(GLOB_RECURSE SRC_FILES "${SRC_DIR}/*.cpp")

add_executable(${PROJECT_EXEC} "${SRC_FILES}")
target_link_libraries(${PROJECT_EXEC} pugixml)
