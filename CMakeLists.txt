cmake_minimum_required(VERSION 3.0.0)
project(socket_servers VERSION 0.1.0)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_STANDARD 11)
if(WIN32)
    set(boost "C:\\msys64\\mingw64\\include")
else()
set(boost "/usr/local/include")
endif()



set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/runtime)
include_directories(BEFORE ${boost} ${PROJECT_SOURCE_DIR}/include)

file(GLOB_RECURSE SOURCE "source/*.cpp" "source/*.c")
add_executable(socket_servers main.cpp)
target_link_libraries(socket_servers PUBLIC ws2_32 wsock32)