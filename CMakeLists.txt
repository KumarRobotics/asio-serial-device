cmake_minimum_required(VERSION 2.8.3)
project(asio_serial_device)

find_package(catkin REQUIRED)
find_package(Boost REQUIRED COMPONENTS thread system)

include_directories(include ${catkin_INCLUDE_DIRS})

catkin_package(
  INCLUDE_DIRS include
  LIBRARIES asio_serial_device
  CATKIN_DEPENDS
  DEPENDS)

add_library(asio_serial_device src/ASIOSerialDevice.cc)
target_link_libraries(asio_serial_device ${Boost_SYSTEM_LIBRARY} ${Boost_THREAD_LIBRARY})

install(TARGETS ${PROJECT_NAME}
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

install(DIRECTORY include/${PROJECT_NAME}/
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
)
