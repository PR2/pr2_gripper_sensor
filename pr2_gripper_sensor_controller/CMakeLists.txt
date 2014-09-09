# Catkin User Guide: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/user_guide.html
# Catkin CMake Standard: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/standards.html
cmake_minimum_required(VERSION 2.8.3)
project(pr2_gripper_sensor_controller)
# Load catkin and all dependencies required for this package
# TODO: remove all from COMPONENTS that are not catkin packages.
find_package(catkin REQUIRED COMPONENTS pr2_controller_interface pr2_mechanism_model pr2_controllers_msgs realtime_tools pluginlib actionlib_msgs roscpp roslib std_msgs std_srvs pr2_gripper_sensor_msgs pr2_controller_manager)

include_directories(include ${catkin_INCLUDE_DIRS})
include_directories(include ${Boost_INCLUDE_DIRS})
link_directories(${catkin_INCLUDE_DIRS})

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

catkin_package(
    DEPENDS pr2_controller_interface pr2_mechanism_model pr2_controllers_msgs realtime_tools pluginlib actionlib_msgs roscpp roslib std_msgs std_srvs pr2_gripper_sensor_msgs pr2_controller_manager
    CATKIN_DEPENDS # TODO
    INCLUDE_DIRS include # TODO include
    LIBRARIES # TODO
)

add_library(pr2_gripper_sensor_controller_lib src/digitalFilter.cpp
                                             src/pr2_gripper_sensor_controller.cpp
                                             src/pressure_observer.cpp
                                             src/acceleration_observer.cpp)

target_link_libraries(pr2_gripper_sensor_controller_lib ${catkin_LIBRARIES})
add_dependencies(pr2_gripper_sensor_controller_lib ${catkin_EXPORTED_TARGETS})