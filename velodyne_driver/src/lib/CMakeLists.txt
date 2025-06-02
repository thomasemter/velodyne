add_library(velodyne_input SHARED input.cpp)

target_link_libraries(velodyne_input
  ${libpcap_LIBRARIES}
  ${velodyne_msgs_TARGETS}
  rclcpp::rclcpp
)

install(TARGETS velodyne_input
  LIBRARY DESTINATION lib
)
