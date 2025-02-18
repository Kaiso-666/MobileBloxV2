cmake_minimum_required(VERSION 3.10)
project(MyAndroidLibrary CXX)

# Specify the Android NDK toolchain
set(CMAKE_TOOLCHAIN_FILE $ENV{ANDROID_NDK}/build/cmake/android.toolchain.cmake)
set(ANDROID_NATIVE_API_LEVEL 21)  # Set the minimum API level

# Add your source files
set(SOURCES
    src/main.cpp
    # Add other source files here
)

# Include headers if necessary
include_directories(include)

# Create the shared library (shared object)
add_library(my_android_lib SHARED ${SOURCES})

# Set the output name
set_target_properties(my_android_lib PROPERTIES OUTPUT_NAME "libmyandroidlib")