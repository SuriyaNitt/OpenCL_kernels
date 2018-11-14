cmake_minimum_required(VERSION 3.5)

project(OPENCL_KERNELS)

find_package(OpenCV REQUIRED)
find_package(OpenCL REQUIRED)

message(STATUS "OpenCV library status:")
message(STATUS "    version: ${OpenCV_VERSION}")
message(STATUS "    libraries: ${OpenCV_LIBS}")
message(STATUS "    include path: ${OpenCV_INCLUDE_DIRS}")

message(STATUS "OpenCL library status:")
message(STATUS "    version: ${OpenCL_VERSION}")
message(STATUS "    libraries: ${OpenCL_LIBS}")
message(STATUS "    include path: ${OpenCL_INCLUDE_DIRS}")


if(CMAKE_VERSION VERSION_LESS "2.8.11")
  # Add OpenCV headers location to your include paths
  include_directories(${OpenCV_INCLUDE_DIRS})
  include_directories(${OpenCL_INCLUDE_DIRS})
endif()

# Declare the executable target built from your sources
add_executable(opencl_test main.cpp)

# Link your application with OpenCV libraries
target_link_libraries(opencl_test ${OpenCV_LIBS} ${OpenCL_LIBS})