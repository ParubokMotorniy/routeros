cmake_minimum_required(VERSION 3.2)

set(PROJECT_NAME nvr_rev_shell)
set(CXX_STANDARD 20)
project(${PROJECT_NAME})

set(CMAKE_CXX_FLAGS "-g -O2 -std=c++17 -Wall -Wextra -Weffc++ -Wshadow -Wcast-align -Wcast-qual -Woverloaded-virtual -Wstrict-null-sentinel -Wswitch-default -Winit-self -Wlogical-op -Wno-deprecated-declarations")

find_package(Boost 1.66 COMPONENTS program_options system regex REQUIRED)

include_directories(SYSTEM ${Boost_INCLUDE_DIR})
include_directories(../../common/)

add_executable(${PROJECT_NAME}
    src/main.cpp
    ../../common/md5.cpp
    ../../common/session.cpp
    ../../common/winbox_session.cpp
    ../../common/winbox_message.cpp)

target_link_libraries(${PROJECT_NAME} ${Boost_LIBRARIES} -lpthread)
