cmake_minimum_required(VERSION 2.8.3)
project(pointcloud_tools)

find_package(catkin REQUIRED COMPONENTS roscpp pcl_ros std_msgs sensor_msgs )
find_package(pcl REQUIRED )

catkin_package()

include_directories(/usr/include/vtk-5.8 ${catkin_INCLUDE_DIRS} ${pcl_INCLUDE_DIRS})

add_executable(pointcloud_mapper src/pointcloud_mapper.cpp)
add_executable(pointcloud_filtering src/pointcloud_filtering.cpp)
add_executable(pcd_publisher src/pcd_publisher.cpp)
add_executable(pointcloud_viewer src/pointcloud_viewer.cpp)

target_link_libraries(pointcloud_viewer ${PCL_LIBRARIES} ${catkin_LIBRARIES} libvtkCommon.so libvtkFiltering.so libvtkRendering.so)
target_link_libraries(pcd_publisher ${PCL_LIBRARIES} ${catkin_LIBRARIES})
target_link_libraries(pointcloud_mapper ${PCL_LIBRARIES} ${catkin_LIBRARIES})
target_link_libraries(pointcloud_filtering ${PCL_LIBRARIES} ${catkin_LIBRARIES})
