cmake_minimum_required(VERSION 2.8.3)
project(asio-serial-device)

find_package(catkin REQUIRED)
find_package(Boost REQUIRED COMPONENTS thread system)

include_directories(include ${catkin_INCLUDE_DIRS})

catkin_package(
    DEPENDS
    CATKIN_DEPENDS # TODO
    INCLUDE_DIRS include
    LIBRARIES # TODO
)

add_library(asio_serial_device src/ASIOSerialDevice.cc)

target_link_libraries(asio_serial_device ${Boost_SYSTEM_LIBRARY} ${Boost_THREAD_LIBRARY})