cmake_minimum_required (VERSION 3.1)
set (CMAKE_CXX_STANDARD 11)
set (CMAKE_BUILD_TYPE Release)

set(CMAKE_CXX_FLAGS "-Wall -Wextra")
set(CMAKE_CXX_FLAGS "-Wno-unknown-pragmas")
set(CMAKE_CXX_FLAGS "-g -O3")

project (ti4-map-generator)

add_subdirectory(
	./backward-cpp
)

include_directories(
	./
	./include
)

add_executable(ti4-map-generator
	./ti4-map-generator.cpp
	${BACKWARD_ENABLE}
)

target_link_libraries(ti4-map-generator
	dl
	)

add_backward(ti4-map-generator)

set( CMAKE_EXPORT_COMPILE_COMMANDS ON )
