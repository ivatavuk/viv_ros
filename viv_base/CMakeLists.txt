cmake_minimum_required(VERSION 2.8.3)
project(viv_base)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
add_compile_options(-Wall -Wextra)

find_package(catkin REQUIRED COMPONENTS controller_manager hardware_interface
   roslaunch roslint roscpp sensor_msgs)
find_package(Boost REQUIRED COMPONENTS chrono)

catkin_package(
    INCLUDE_DIRS include
    CATKIN_DEPENDS hardware_interface roscpp sensor_msgs
    DEPENDS Boost
)

include_directories(include ${Boost_INCLUDE_DIRS} ${catkin_INCLUDE_DIRS})

add_executable(viv_base
  src/viv_base.cpp
  src/viv_hardware.cpp)

target_link_libraries(viv_base ${catkin_LIBRARIES} ${Boost_LIBRARIES})


