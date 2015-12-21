cmake_minimum_required(VERSION 2.8.3)
project(object_manipulation_msgs)

find_package(catkin REQUIRED COMPONENTS
  actionlib_msgs
  std_msgs
  geometry_msgs
  sensor_msgs
  trajectory_msgs
  sensor_msgs
  household_objects_database_msgs
  arm_navigation_msgs
  message_generation)

add_message_files(
  FILES
  CartesianGains.msg
  ClusterBoundingBox.msg
  Grasp.msg
  GraspPlanningErrorCode.msg
  GraspResult.msg
  GraspableObject.msg
  GraspableObjectList.msg
  GripperTranslation.msg
  ManipulationPhase.msg
  ManipulationResult.msg
  PlaceLocationResult.msg
  SceneRegion.msg
)

add_service_files(
  FILES
  FindClusterBoundingBox2.srv
  FindClusterBoundingBox.srv
  GraspPlanning.srv
  GraspStatus.srv
  PlacePlanning.srv
  ReactiveGrasp.srv
)

add_action_files(
  FILES
  FindContainer.action
  GraspPlanning.action
  Place.action
  ReactiveLift.action
  GraspHandPostureExecution.action
  Pickup.action
  ReactiveGrasp.action
  ReactivePlace.action
)

generate_messages(
  DEPENDENCIES
  actionlib_msgs
  std_msgs
  geometry_msgs
  trajectory_msgs
  sensor_msgs
  arm_navigation_msgs
  household_objects_database_msgs
)

catkin_package(
    INCLUDE_DIRS include
    CATKIN_DEPENDS actionlib_msgs std_msgs geometry_msgs sensor_msgs trajectory_msgs sensor_msgs arm_navigation_msgs household_objects_database_msgs
)

install(DIRECTORY include/${PROJECT_NAME}/
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
  PATTERN ".svn" EXCLUDE)
