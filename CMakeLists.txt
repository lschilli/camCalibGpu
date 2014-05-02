# Copyright (C) 2007 RobotCub Consortium
# Author: Jonas Ruesch
# CopyPolicy: Released under the terms of the GNU GPL v2.0.
cmake_minimum_required(VERSION 2.8)

SET(PROJECTNAME camCalibGpu)
PROJECT(${PROJECTNAME})

FIND_PACKAGE(YARP REQUIRED)
FIND_PACKAGE(OpenCV REQUIRED)

SET(folder_source src/main.cpp
                  src/CamCalibModule.cpp
				  src/CalibToolFactory.cpp
				  src/PinholeCalibTool.cpp)
				  
SET(folder_header include/iCub/CamCalibModule.h
                   include/iCub/CalibToolFactory.h
				   include/iCub/ICalibTool.h
				   include/iCub/PinholeCalibTool.h)

SOURCE_GROUP("Source Files" FILES ${folder_source})
SOURCE_GROUP("Header Files" FILES ${folder_header})

INCLUDE_DIRECTORIES(${PROJECT_SOURCE_DIR}/include
                    ${OpenCV_INCLUDE_DIRS}
                    ${YARP_INCLUDE_DIRS})

ADD_EXECUTABLE(${PROJECTNAME} ${folder_source} ${folder_header})



TARGET_LINK_LIBRARIES(${PROJECTNAME} ${OpenCV_LIBRARIES}
                                     ${YARP_LIBRARIES})

INSTALL(TARGETS ${PROJECTNAME} DESTINATION bin)

