cmake_minimum_required(VERSION 3.0.2)
project(mmm_robot)

## Compile as C++11, supported in ROS Kinetic and newer
add_compile_options(-std=c++11)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS roscpp rospy std_msgs genmsg)

## Generate added messages and services
generate_messages(DEPENDENCIES std_msgs)

catkin_package()

include_directories(
  include
  ${catkin_INCLUDE_DIRS}
)

install(DIRECTORY config
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})

install(DIRECTORY launch
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})

include_directories(include ${catkin_INCLUDE_DIRS})

add_executable(mmm_robot_interface src/mmm_robot_interface.cpp src/torque_calculater.cpp)
target_link_libraries(mmm_robot_interface ${catkin_LIBRARIES})
