cmake_minimum_required(VERSION 2.8.12)  # Ships with Ubuntu 14.04 (Trusty)

project(cartographer_turtlebot)

set(PACKAGE_DEPENDENCIES
  cartographer_ros
  roscpp
  roslib
  sensor_msgs
)

find_package(cartographer REQUIRED)
include("${CARTOGRAPHER_CMAKE_DIR}/functions.cmake")
google_initialize_cartographer_project()
google_enable_testing()

find_package(LuaGoogle REQUIRED)

find_package(catkin REQUIRED COMPONENTS ${PACKAGE_DEPENDENCIES})

# Override Catkin's GTest configuration to use GMock.
set(GTEST_FOUND TRUE)
set(GTEST_INCLUDE_DIRS ${GMOCK_INCLUDE_DIRS})
set(GTEST_LIBRARIES ${GMOCK_LIBRARIES})

catkin_package(CATKIN_DEPENDS message_runtime ${PACKAGE_DEPENDENCIES})

add_executable(cartographer_flat_world_imu_node "cartographer_turtlebot/flat_world_imu_node_main.cc")
target_include_directories(cartographer_flat_world_imu_node SYSTEM PUBLIC ${catkin_INCLUDE_DIRS})
target_link_libraries(cartographer_flat_world_imu_node ${catkin_LIBRARIES})
add_dependencies(cartographer_flat_world_imu_node ${catkin_EXPORTED_TARGETS})
set(TARGET_COMPILE_FLAGS "${TARGET_COMPILE_FLAGS} ${GOOG_CXX_FLAGS}")
set_target_properties(cartographer_flat_world_imu_node PROPERTIES COMPILE_FLAGS ${TARGET_COMPILE_FLAGS})

install(TARGETS cartographer_flat_world_imu_node
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

install(DIRECTORY launch configuration_files
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)
