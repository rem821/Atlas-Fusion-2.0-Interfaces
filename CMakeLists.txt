cmake_minimum_required(VERSION 3.22.1)
project(atlas_fusion_interfaces)

# Use C++ 20
SET(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++20")

# Turn on all possible warnings during build
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wextra -Wpedantic")

# Setup Debug and Release flags
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -g")
set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} -O3")

find_package(ament_cmake REQUIRED)

find_package(std_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)

find_package(rosidl_default_generators REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME}
        "msg/CameraData.msg"
        "msg/LidarData.msg"
        "msg/YoloDetection.msg"
        "msg/ImuDquatData.msg"
        "msg/ImuGnssData.msg"
        "msg/ImuImuData.msg"
        "msg/ImuMagData.msg"
        "msg/ImuPressureData.msg"
        "msg/ImuTempData.msg"
        "msg/ImuTimeData.msg"
        "msg/GnssPositionData.msg"
        "msg/GnssTimeData.msg"
        "msg/RadarDetection.msg"
        "msg/RadarData.msg"
        DEPENDENCIES std_msgs sensor_msgs geometry_msgs
        )

ament_export_dependencies(rosidl_default_runtime)

ament_package()