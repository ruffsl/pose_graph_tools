cmake_minimum_required(VERSION 3.5)

project(pose_graph_tools)

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(rosidl_default_generators REQUIRED)

find_package(std_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(visualization_msgs REQUIRED)
find_package(interactive_markers REQUIRED)

set(msg_files
  "msg/PoseGraph.msg"
  "msg/PoseGraphEdge.msg"
  "msg/PoseGraphNode.msg")

rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
  DEPENDENCIES
  builtin_interfaces
  std_msgs
  geometry_msgs)

# cs_add_library(${PROJECT_NAME}
#   src/visualizer.cpp
# )

# cs_add_executable(visualizer_node
#   src/visualizer_node.cpp
#   src/visualizer.cpp
# )

install(DIRECTORY launch
  DESTINATION share/${PROJECT_NAME})

ament_package()
