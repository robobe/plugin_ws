cmake_minimum_required(VERSION 3.8)
project(polygon_usage)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(pluginlib REQUIRED)
find_package(polygon_base REQUIRED)

add_executable(area_node src/area_node.cpp)
ament_target_dependencies(
  area_node
  "pluginlib"
  "polygon_base"
)

install(TARGETS area_node
  DESTINATION lib/${PROJECT_NAME})



ament_package()
