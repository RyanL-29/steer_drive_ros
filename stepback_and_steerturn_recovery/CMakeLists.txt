cmake_minimum_required(VERSION 2.8.3)
project(stepback_and_steerturn_recovery)

find_package(catkin REQUIRED
        COMPONENTS
            cmake_modules
            roscpp
            tf2
            tf2_geometry_msgs
            tf2_ros
            costmap_2d
            nav_core
            pluginlib
            base_local_planner
            geometry_msgs
        )

find_package(Eigen REQUIRED)
include_directories(
    include
    ${catkin_INCLUDE_DIRS}
    ${EIGEN_INCLUDE_DIRS}
)
add_definitions(${EIGEN_DEFINITIONS})

catkin_package(
    CATKIN_DEPENDS
        roscpp
        pluginlib
)

add_library(${PROJECT_NAME} src/stepback_and_steerturn_recovery.cpp)
target_link_libraries(${PROJECT_NAME} ${catkin_LIBRARIES})

install(TARGETS ${PROJECT_NAME}
       LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
       )

install(FILES stepback_and_steerturn_recovery_plugin.xml
    DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)
