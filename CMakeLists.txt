
cmake_minimum_required(VERSION 3.24)
project(VulkanGoPro LANGUAGES C CXX)

# Chuẩn C++
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# 1) Tìm Vulkan SDK (qua FindVulkan.cmake của Khronos hoặc CMake config)
find_package(Vulkan REQUIRED)

# 2) Tìm lib qua vcpkg (CONFIG mode)
find_package(glfw3 CONFIG REQUIRED)   # target: glfw
find_package(glm CONFIG REQUIRED)     # target: glm::glm

# 3) Executable
add_executable(VulkanGoPro
  main.cpp   # nên để source trong thư mục src/
)

# 4) Include directory (nếu cần thêm include của Vulkan SDK)
#    Thường không cần vì Vulkan::Vulkan đã có sẵn include path.
# target_include_directories(VulkanGoPro PRIVATE ${Vulkan_INCLUDE_DIRS})

# 5) Link libraries
target_link_libraries(VulkanGoPro PRIVATE
  Vulkan::Vulkan
  glfw
  glm::glm
)

# 6) (Tùy chọn) Define macro cho vulkan-hpp
target_compile_definitions(VulkanGoPro PRIVATE
VULKAN_HPP_DISPATCH_LOADER_DYNAMIC=1
        VULKAN_HPP_NO_STRUCT_CONSTRUCTORS=1)

