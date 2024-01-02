cmake_minimum_required(VERSION 3.17)
set(CMAKE_CXX_STANDARD 17)

set(CMAKE_CXX_STANDARD_REQUIRED ON)
project(AIDenoiser VERSION 1.0 LANGUAGES CUDA CXX)

set(CUDA_INCLUDE "/opt/cuda/include")
set(OPTIX_INCLUDE "/home/marius/Downloads/optixSDK/include")

find_package(OpenImageIO REQUIRED)
find_package(CUDA REQUIRED)

add_executable(denoiser src/main.cpp)
target_include_directories(denoiser PRIVATE ${CMAKE_CURRENT_SOURCE_DIR} ${OpenImageIO_INCLUDE_DIR} ${CUDA_INCLUDE} ${OPTIX_INCLUDE})
target_link_libraries(denoiser PRIVATE ${CUDA_LIBRARIES} OpenImageIO)
