cmake_minimum_required(VERSION 2.8.3)
project(canny_edge_my_face)

find_package(catkin REQUIRED COMPONENTS cv_bridge image_transport roscpp sensor_msgs std_msgs message_generation)
find_package(OpenCV REQUIRED)

#add_message_files(
#  FILES
#)

generate_messages(
  DEPENDENCIES
  canny_edge_my_face
)


include_directories(include
  ${catkin_INCLUDE_DIRS}
  ${OpenCV_INCLUDE_DIRS}
)

catkin_package(
   INCLUDE_DIRS include
  LIBRARIES canny_edge_my_face
  CATKIN_DEPENDS cv_bridge image_transport opencv2 roscpp sensor_msgs std_msgs message_runtime
  DEPENDS system_lib
   CATKIN_DEPENDS message_runtime
)


add_executable(simpleCanny src/face_Canny.cpp)
target_link_libraries(simpleCanny ${OpenCV_LIBRARIES} ${catkin_LIBRARIES} )


