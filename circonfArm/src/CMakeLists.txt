# # Copyright: 2012 iCub Facility, Istituto Italiano di Tecnologia
# # Author: Lorenzo Natale
# # CopyPolicy: Released under the terms of the GNU GPL v2.0.
# # 
# 
# CMAKE_MINIMUM_REQUIRED(VERSION 2.6)
# SET(PROJECTNAME circonfArm)
# PROJECT(${PROJECTNAME})
# 
# find_package(YARP)
# find_package(ICUB)
# set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${YARP_MODULE_PATH})
# set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${ICUB_MODULE_PATH})
# 
# include_directories(${ICUB_INCLUDE_DIRS} ${YARP_INCLUDE_DIRS})
# 
# add_executable(${PROJECTNAME} main.cpp)
# target_link_libraries(${PROJECTNAME} ${YARP_LIBRARIES})
# 
# install(TARGETS ${PROJECTNAME} RUNTIME DESTINATION ${CMAKE_CURRENT_SOURCE_DIR}/../bin)


# Copyright: 2015 iCub Facility, Istituto Italiano di Tecnologia
# Author: Raffaello Camoriano
# CopyPolicy: Released under the terms of the GNU GPL v2.0.
# 

CMAKE_MINIMUM_REQUIRED(VERSION 2.6)
SET(PROJECTNAME circonfArm)
PROJECT(${PROJECTNAME})

# find_package(YARP)
# find_package(ICUB)

file(GLOB source main.cpp syncEst.cpp)
#file(GLOB header include/*.h)

source_group("Source Files" FILES ${source})
#source_group("Header Files" FILES ${header})

include_directories(${YARP_INCLUDE_DIRS} ${ICUB_INCLUDE_DIRS})

add_executable(${PROJECTNAME} main.cpp)
add_executable(syncEst syncEst.cpp)
target_link_libraries(${PROJECTNAME}  ${YARP_LIBRARIES})
target_link_libraries(syncEst  ${YARP_LIBRARIES}
                               ctrlLib)
# target_link_libraries(${PROJECTNAME} ${Gurls_LIBRARIES})

# install(TARGETS ${PROJECTNAME} RUNTIME DESTINATION ${CMAKE_CURRENT_SOURCE_DIR}/../bin)
install(TARGETS ${PROJECTNAME} syncEst DESTINATION bin)

##Debug: Print out all variables
# get_cmake_property(_variableNames VARIABLES)
# foreach (_variableName ${_variableNames})
    # message(STATUS "${_variableName}=${${_variableName}}")
# endforeach()

#install(TARGETS ${PROJECTNAME} RUNTIME DESTINATION ${CMAKE_CURRENT_SOURCE_DIR}/../bin)

# yarp_install(FILES ${PROJECTNAME}.xml DESTINATION ${ICUBCONTRIB_MODULES_INSTALL_DIR})
