cmake_minimum_required(VERSION 2.8.3)
project(rqt_system_control)


find_package(Qt4 COMPONENTS QtCore QtGui REQUIRED)

include(${QT_USE_FILE})

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS
  rospy
  rqt_gui
  rqt_gui_py
  rqt_gui_cpp
)



set(rqt_system_control_SRCS
  src/rqt_system_control/rqt_system_control.cpp
)

set(rqt_system_control_HDRS
  include/rqt_system_control/rqt_system_control.h

)

set(rqt_system_control_UIS
  resource/rqt_system_control.ui
)

set(rqt_system_control_INCLUDE_DIRECTORIES
  include
  ${CMAKE_CURRENT_BINARY_DIR}
)


catkin_package(
  INCLUDE_DIRS ${rqt_system_control_INCLUDE_DIRECTORIES}
  LIBRARIES ${PROJECT_NAME}
  CATKIN_DEPENDS rospy rqt_gui rqt_gui_py
#  DEPENDS system_lib
)
#catkin_python_setup()

#SET(CMAKE_AUTOUIC ON)  


qt4_wrap_cpp(rqt_system_control_MOCS ${rqt_system_control_HDRS})
qt4_wrap_ui(rqt_system_control_UIS_H ${rqt_system_control_UIS})

include_directories(${rqt_system_control_INCLUDE_DIRECTORIES} ${catkin_INCLUDE_DIRS} )
add_library(${PROJECT_NAME} ${rqt_system_control_SRCS} ${rqt_system_control_MOCS} ${rqt_system_control_UIS_H})
target_link_libraries(${PROJECT_NAME} ${catkin_LIBRARIES} ${QT_QTCORE_LIBRARY} ${QT_QTGUI_LIBRARY})


