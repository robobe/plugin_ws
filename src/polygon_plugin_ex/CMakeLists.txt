cmake_minimum_required(VERSION 3.8)
project(polygon_plugin_ex)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(ament_cmake_ros REQUIRED)
find_package(polygon_base REQUIRED)
find_package(pluginlib REQUIRED)

add_library(${PROJECT_NAME} src/polygon_plugins.cpp)
ament_target_dependencies(
  ${PROJECT_NAME}
  polygon_base
  pluginlib
)

pluginlib_export_plugin_description_file(polygon_base plugins.xml)

install(
  TARGETS ${PROJECT_NAME}
  EXPORT export_${PROJECT_NAME}
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
  RUNTIME DESTINATION bin
)

ament_export_libraries(
  ${PROJECT_NAME}
)
ament_export_targets(
  export_${PROJECT_NAME}
)
ament_package()
