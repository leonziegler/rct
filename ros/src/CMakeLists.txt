cmake_minimum_required(VERSION 2.6)
          
# --- generate executable
INCLUDE_DIRECTORIES(${CMAKE_SOURCE_DIR}/core/src ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_BINARY_DIR})
ADD_LIBRARY(${RCT_NAME_ROS} SHARED rct/impl/TransformCommRos.cpp rct/impl/TransformListenerRos.cpp)
TARGET_LINK_LIBRARIES(${RCT_NAME_ROS} ${ROS_CPP_LIBRARIES} ${RCT_NAME})
SET_TARGET_PROPERTIES(${RCT_NAME_ROS} PROPERTIES
                                 VERSION ${RCT_VERSION}
                                 SOVERSION ${RCT_API_VERSION})

# --- install target
INSTALL(TARGETS ${RCT_NAME_ROS}
        LIBRARY DESTINATION ${LIBDIR})
INSTALL(DIRECTORY . DESTINATION ${INCLUDEDIR}
          FILES_MATCHING 
          PATTERN "./rct/impl/*.h" 
)
