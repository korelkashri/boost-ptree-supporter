cmake_minimum_required(VERSION 3.12)
set(PROJECT_NAME BOOSTPtreeSupporter)
project(${PROJECT_NAME})

set(BOOST_REQUIRED_COMPONENTS
        system
        thread
        regex
        coroutine
        context
        filesystem
        date_time
        unit_test_framework
        program_options
        )
find_package(Boost "1.58.0" REQUIRED ${BOOST_REQUIRED_COMPONENTS})
include_directories(SYSTEM ${Boost_INCLUDE_DIRS})
link_directories(${Boost_LIBRARY_DIRS})

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++2a")

file(GLOB_RECURSE SOURCES RELATIVE ${CMAKE_SOURCE_DIR} "src/*")

add_executable(${PROJECT_NAME} ${SOURCES})

target_link_libraries(${PROJECT_NAME} ${Boost_LIBRARIES})