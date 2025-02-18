cmake_minimum_required(VERSION 3.10)
project(MyAndroidLibrary CXX)

# Specify the Android NDK toolchain
set(CMAKE_TOOLCHAIN_FILE $ENV{ANDROID_NDK}/build/cmake/android.toolchain.cmake)
set(ANDROID_NATIVE_API_LEVEL 21)  # Set the minimum API level

# Specify Lua headers and libraries (ensure that Lua is included)
# If Lua is installed in the system, you might specify the path to its include and lib directories
include_directories(${CMAKE_SOURCE_DIR}/include)  # Adjust path to Lua include directory if needed
link_directories(${CMAKE_SOURCE_DIR}/lib)  # Adjust path to Lua library directory if needed

# Add your source files
set(SOURCES
    NativeLib/main.cpp
    # Add other source files here
)

# Create the shared library (shared object)
add_library(my_android_lib SHARED ${SOURCES})

# Link Lua library (if Lua is used in the project)
target_link_libraries(my_android_lib lua5.3)  # Replace with correct Lua library name (e.g., lua or lua5.3)

# Set the output name
set_target_properties(my_android_lib PROPERTIES OUTPUT_NAME "libmyandroidlib")

# Optional: Set C++ standard to 17 for C++17 features
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)