cmake_minimum_required(VERSION 3.10)
project(raylib_project)

#C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

#Build raylib
set(BUILD_EXAMPLES OFF CACHE BOOL "" FORCE) # Don't build examples
set(BUILD_GAMES    OFF CACHE BOOL "" FORCE) # Don't build games
add_subdirectory(external/raylib)


#Source files
file(GLOB_RECURSE SOURCES "src/*.cpp")

#Create executable
add_executable(${PROJECT_NAME} ${SOURCES})

#Link libraries
target_link_libraries(${PROJECT_NAME} raylib)

#Include directories
target_include_directories(${PROJECT_NAME} PRIVATE 
    ${PROJECT_SOURCE_DIR}/external/source_group
)