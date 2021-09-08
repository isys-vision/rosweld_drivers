cmake_minimum_required(VERSION 2.8.3)
project(rosweld_drivers)

find_package(catkin REQUIRED COMPONENTS
  std_msgs
  geometry_msgs
  industrial_msgs
  message_generation
)

add_message_files(
   DIRECTORY msg
   FILES
   Status.msg
   WeldingJobs.msg
   RobotState.msg
   WeldingState.msg
   Move.msg
   MoveJoints.msg
   EulerAngles.msg
 )

add_service_files(FILES
  SendStatus.srv
  SetJobNumber.srv
  SetWeldingParameters.srv
  MoveAlong.srv
  MoveAlongJoints.srv
  SetSpeed.srv
  MoveBetween.srv
  Input.srv
  SetIO.srv
)

generate_messages(
  DEPENDENCIES
  std_msgs
  geometry_msgs
  industrial_msgs
)

catkin_package(
  CATKIN_DEPENDS message_runtime std_msgs geometry_msgs industrial_msgs
)
