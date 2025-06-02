add_library(velodyne_rawdata SHARED
  rawdata.cpp
  calibration.cpp)
target_link_libraries(velodyne_rawdata
  ${geometry_msgs_TARGETS}
  ${sensor_msgs_TARGETS}
  ${velodyne_msgs_TARGETS}
  angles::angles
  rclcpp::rclcpp
  sensor_msgs::sensor_msgs_library
  tf2::tf2
  tf2_ros::static_transform_broadcaster_node
  tf2_ros::tf2_ros
)

target_link_libraries(velodyne_rawdata
  ${PCL_LIBRARIES}
)

target_link_libraries(velodyne_rawdata
        ${YAML_CPP_LIBRARIES})

add_library(velodyne_cloud_types SHARED
  pointcloudXYZIRT.cpp
  organized_cloudXYZIRT.cpp
)
target_link_libraries(velodyne_cloud_types
  ${sensor_msgs_TARGETS}
  ${velodyne_msgs_TARGETS}
  rclcpp::rclcpp
  sensor_msgs::sensor_msgs_library
  tf2_ros::static_transform_broadcaster_node
  tf2_ros::tf2_ros
)

target_link_libraries(velodyne_cloud_types
  ${PCL_LIBRARIES}
)

install(TARGETS velodyne_cloud_types velodyne_rawdata
  RUNTIME DESTINATION bin
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib)
