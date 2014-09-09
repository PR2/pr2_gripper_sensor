cmake_minimum_required(VERSION 2.8.3)
project(pr2_gripper_sensor_msgs)
find_package(catkin REQUIRED COMPONENTS roscpp actionlib_msgs actionlib message_generation std_msgs)

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

add_message_files(DIRECTORY msg
  FILES
  PR2GripperEventDetectorCommand.msg
  PR2GripperEventDetectorData.msg
  PR2GripperFindContactCommand.msg
  PR2GripperFindContactData.msg
  PR2GripperPressureData.msg
  PR2GripperReleaseCommand.msg
  PR2GripperReleaseData.msg
  PR2GripperSensorRawData.msg
  PR2GripperSensorRTState.msg
  PR2GripperSlipServoCommand.msg
  PR2GripperSlipServoData.msg
  PR2GripperGrabData.msg
  PR2GripperGrabCommand.msg
  PR2GripperForceServoCommand.msg
  PR2GripperForceServoData.msg
)


add_action_files(DIRECTORY action
  FILES
  PR2GripperEventDetector.action
  PR2GripperFindContact.action
  PR2GripperForceServo.action
  PR2GripperGrab.action
  PR2GripperRelease.action
  PR2GripperSlipServo.action
)

include_directories(${catkin_INCLUDE_DIRS})
link_directories(${catkin_INCLUDE_DIRS})
generate_messages(
    DEPENDENCIES std_msgs actionlib_msgs#TODO DEPENDENCIES geometry_msgs std_msgs
)

catkin_package(
    DEPENDS include roscpp actionlib_msgs actionlib std_msgs
    CATKIN_DEPENDS actionlib_msgs message_runtime# TODO
    INCLUDE_DIRS ${catkin_INCLUDE_DIRS}# TODO include
    LIBRARIES # TODO
)

