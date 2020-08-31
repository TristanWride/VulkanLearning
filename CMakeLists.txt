cmake_minimum_required(VERSION 3.12)
project(VulkanLearning)

set(CMAKE_CXX_STANDARD 17)

# Vulkan needs to be installed
find_package(Vulkan REQUIRED)

# Turn off development building for glfw
set(GLFW_BUILD_DOCS     OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS    OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
add_subdirectory(lib/glfw)

add_subdirectory(src)
add_executable(vlearning ${VLEARNING_SOURCES})
target_link_libraries(vlearning glfw ${GLFW_LIBRARIES} Vulkan::Vulkan)
target_include_directories(
  vlearning
  PRIVATE
  ${CMAKE_CURRENT_SOURCE_DIR}/include
)
