cmake_minimum_required(VERSION 3.4)

set(PROJ_NAME skeleton)
set(MODULE_A liba)

project(${PROJ_NAME})

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_FLAGS "-g -Werror -Wpedantic -Wall")

set(BASEPATH "${CMAKE_SOURCE_DIR}")
include_directories("${BASEPATH}")

#Command below is used for compile_commands.json which can be processed by YCM vim plugin
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

#If compile_commands.json is created provision that file property by direct copy
#to the current source directory
IF( EXISTS "${CMAKE_CURRENT_BINARY_DIR}/compile_commands.json" )
	EXECUTE_PROCESS( COMMAND ${CMAKE_COMMAND} -E copy_if_different
					${CMAKE_CURRENT_BINARY_DIR}/compile_commands.json
					${CMAKE_CURRENT_SOURCE_DIR}/.compile_commands.json
					)
ENDIF()

#Commands below force explicit dependency for GTest framework
find_package(GTest REQUIRED)
include_directories(${GTEST_INCLUDE_DIRS})
enable_testing()

#Commands below force explicit dependency for a GMock framework.
# and rely on a supplied cmake module.
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake/Modules/")
find_package(GMock REQUIRED)
include_directories(${GMOCK_INCLUDE_DIRS})

add_subdirectory(main)
add_subdirectory(tests)
add_subdirectory(${MODULE_A})
