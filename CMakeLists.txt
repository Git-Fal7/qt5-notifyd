cmake_minimum_required (VERSION 3.8.2)
set(PROJECT qt5-notifyd)
project(${PROJECT})

# Find includes in the build directories
set(CMAKE_INCLUDE_CURRENT_DIR ON)

# Turn on automatic invocation of the MOC, UIC & RCC
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTORCC ON)

# Dependencies
find_package(Qt5 REQUIRED COMPONENTS Widgets DBus)

# Tell CMake to create the executable
add_executable(${PROJECT}
 src/main.cpp
 src/Manager.cpp
 src/Widget.cpp
)

# Add the dependencies for linking
target_link_libraries(${PROJECT}
 PRIVATE
 Qt5::Widgets
 Qt5::DBus
)

set(BIN_LOCATION "${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR}/${PROJECT}/")
configure_file(data/qt5-notifyd.desktop.in qt5-notifyd.desktop @ONLY)

install(TARGETS ${PROJECT} RUNTIME DESTINATION "${BIN_LOCATION}")
install(FILES "${CMAKE_BINARY_DIR}/qt5-notifyd.desktop" DESTINATION "/etc/xdg/autostart")
