cmake_minimum_required(VERSION 3.5)
project(glad_ros)
set(CMAKE_BUILD_TYPE Release)
find_package(catkin)
set(LIBRARY_NAME "${PROJECT_NAME}")
set(SRC_FILES src/glad.c)
catkin_package(
LIBRARIES 
    ${LIBRARY_NAME}
)
add_library(${LIBRARY_NAME} ${SRC_FILES})
target_include_directories(${LIBRARY_NAME} PUBLIC include/)
add_dependencies(${LIBRARY_NAME} ${catkin_EXPORTED_TARGETS}) 
## Mark the library for installations
install(TARGETS 
    ${LIBRARY_NAME}
    ${COMPONENT_NAME}
    ${NODELET_NAME}
    ${NODE_NAME}    
    ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
    LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
    RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

# install header files
install(
    DIRECTORY 
    include/${PROJECT_NAME}/
    DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
    FILES_MATCHING PATTERN "*.h"
)
