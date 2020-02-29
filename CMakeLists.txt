cmake_minimum_required(VERSION 3.15)
project(seed_tester_native)

set(CMAKE_CXX_STANDARD 14)
find_package (Threads)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -ggdb3")

add_executable(seed_tester_native generator.h generator.cpp random.h random.cpp  main.cpp)

target_link_libraries (seed_tester_native ${CMAKE_THREAD_LIBS_INIT})

add_custom_command(
		TARGET seed_tester_native PRE_BUILD
		COMMAND ${CMAKE_COMMAND} -E copy
		${CMAKE_SOURCE_DIR}/seeds0.txt
		${CMAKE_CURRENT_BINARY_DIR}/seeds0.txt)