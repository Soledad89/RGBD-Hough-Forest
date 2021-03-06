cmake_minimum_required ( VERSION 2.8 )

# The name of our project is "evaluate". 
project( evaluate ) 

# cpp flags
SET( CMAKE_CXX_FLAGS "-g -Wno-deprecated-declarations -Wno-deprecated -Wno-unused-result -mssse3 -DEIGEN_NO_DEBUG -fopenmp" )

FIND_PACKAGE( PCL 1.6 REQUIRED )
FIND_PACKAGE( OpenCV 2.4.5 REQUIRED )

# header files *.h
FILE ( GLOB HEADERS ${evaluate_SOURCE_DIR}/*.h )

# source files *.c
FILE ( GLOB SRCS ${evaluate_SOURCE_DIR}/*.cpp )

# set all include directories
INCLUDE_DIRECTORIES ( ${INCLUDE_DIR} ${PCL_INCLUDE_DIRS} ${OPENCV_INCLUDE_DIRS} ${INCLUDE_EIGEN_DIRS} )

# set all libraries
SET ( LIBS ${PCL_COMMON_LIBRARIES} ${PCL_VISUALIZATION_LIBRARIES} ${PCL_SEARCH_LIBRARIES} ${PCL_KDTREE_LIBRARIES} ${PCL_FEATURES_LIBRARIES} ${PCL_SURFACE_LIBRARIES} ${PCL_SEGMENTATION_LIBRARIES} ${PCL_FILTERS_LIBRARIES} ${OpenCV_LIBS} )

# define the executable 
ADD_EXECUTABLE ( evaluate ${SRCS} ${HEADERS} )

# link libraries with executable
TARGET_LINK_LIBRARIES ( evaluate ${LIBS} )

# install binary to set destination
INSTALL_TARGETS(/home/badami/Codes/RGBD_Hough_Forest/evaluation evaluate) 
