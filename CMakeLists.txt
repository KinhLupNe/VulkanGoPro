
cmake_minimum_required(VERSION 3.24)
project(VulkanGoPro LANGUAGES C CXX)

# Chuẩn C++
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# 1) Vulkan: dùng SDK đã cài (FindVulkan)
find_package(Vulkan REQUIRED)

# 2) Các lib qua vcpkg (dùng CONFIG mode)
#    - GLFW:      find_package(glfw3 CONFIG REQUIRED)  -> target: glfw
#    - GLM:       find_package(glm CONFIG REQUIRED)     -> target: glm::glm
find_package(glfw3 CONFIG REQUIRED)
find_package(glm CONFIG REQUIRED)

add_executable(VulkanGoPro
  main.cpp
)

target_link_libraries(VulkanGoPro PRIVATE
  Vulkan::Vulkan
  glfw
  glm::glm
)

