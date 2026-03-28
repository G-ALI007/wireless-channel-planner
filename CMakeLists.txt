cmake_minimum_required(VERSION 3.10)
project(WirelessChannelPlanner VERSION 1.0.0 LANGUAGES CXX)

# Set C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Include directories
include_directories(${PROJECT_SOURCE_DIR}/include)

# Library source files
set(LIBRARY_SOURCES
    src/channel_planner.cpp
)

# Create static library
add_library(wireless_channel_planner STATIC ${LIBRARY_SOURCES})

# Create shared library (optional)
add_library(wireless_channel_planner_shared SHARED ${LIBRARY_SOURCES})
set_target_properties(wireless_channel_planner_shared PROPERTIES OUTPUT_NAME wireless_channel_planner)

# Example executable
add_executable(channel_planner_example examples/example.cpp)
target_link_libraries(channel_planner_example wireless_channel_planner)

# Installation rules
install(TARGETS wireless_channel_planner wireless_channel_planner_shared
        ARCHIVE DESTINATION lib
        LIBRARY DESTINATION lib)

install(FILES include/channel_planner.h DESTINATION include)

# Enable testing
enable_testing()

# Optionally add tests directory if you create tests
# add_subdirectory(tests)

# Print build information
message(STATUS "")
message(STATUS "Wireless Channel Planner Configuration:")
message(STATUS "  Version: ${PROJECT_VERSION}")
message(STATUS "  C++ Standard: ${CMAKE_CXX_STANDARD}")
message(STATUS "  Build Type: ${CMAKE_BUILD_TYPE}")
message(STATUS "")
