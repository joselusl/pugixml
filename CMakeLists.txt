cmake_minimum_required(VERSION 2.8.3)

set(PROJECT_NAME pugixml)
project(${PROJECT_NAME})


### Use version 2011 of C++ (c++11). By default ROS uses c++98
#see: http://stackoverflow.com/questions/10851247/how-to-activate-c-11-in-cmake
#see: http://stackoverflow.com/questions/10984442/how-to-detect-c11-support-of-a-compiler-with-cmake
#add_definitions(-std=c++11)
# add_definitions(-std=c++0x)
add_definitions(-std=c++03)


# Set the build type.  Options are:
#  Coverage       : w/ debug symbols, w/o optimization, w/ code-coverage
#  Debug          : w/ debug symbols, w/o optimization
#  Release        : w/o debug symbols, w/ optimization
#  RelWithDebInfo : w/ debug symbols, w/ optimization
#  MinSizeRel     : w/o debug symbols, w/ optimization, stripped binaries


	
	
set(PUGIXML_LIBRARY_SOURCE_DIR
	src/sources
)

set(PUGIXML_LIBRARY_SOURCE_FILES
	${PUGIXML_LIBRARY_SOURCE_DIR}/pugixml.cpp
)
	
set(PUGIXML_LIBRARY_HEADER_DIR
	src/include
)

set(PUGIXML_LIBRARY_HEADER_FILES
	${PUGIXML_LIBRARY_HEADER_DIR}/pugixml/pugiconfig.hpp
	${PUGIXML_LIBRARY_HEADER_DIR}/pugixml/pugixml.hpp
)


find_package(catkin REQUIRED)

catkin_package(
    INCLUDE_DIRS ${PUGIXML_LIBRARY_HEADER_DIR}
    LIBRARIES ${PROJECT_NAME}
  )



include_directories(${PUGIXML_LIBRARY_HEADER_DIR} ${PUGIXML_LIBRARY_HEADER_DIR}/pugixml)
include_directories(${catkin_INCLUDE_DIRS})


add_library(${PROJECT_NAME} ${PUGIXML_LIBRARY_SOURCE_FILES} ${PUGIXML_LIBRARY_HEADER_FILES})
add_dependencies(${PROJECT_NAME} ${catkin_EXPORTED_TARGETS})
target_link_libraries(${PROJECT_NAME} ${catkin_LIBRARIES})

