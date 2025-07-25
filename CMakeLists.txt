cmake_minimum_required(VERSION 3.16)

project(dummy4 VERSION 0.1 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Qt6 REQUIRED COMPONENTS Quick)

qt_standard_project_setup()

qt_add_executable(appdummy4
    main.cpp
)

qt_add_qml_module(appdummy4
    URI dummy4
    VERSION 1.0
    QML_FILES
        Main.qml
)

set_target_properties(appdummy4 PROPERTIES
    MACOSX_BUNDLE_BUNDLE_VERSION ${PROJECT_VERSION}
    MACOSX_BUNDLE_SHORT_VERSION_STRING ${PROJECT_VERSION_MAJOR}.${PROJECT_VERSION_MINOR}
    MACOSX_BUNDLE TRUE
    WIN32_EXECUTABLE TRUE
)

target_link_libraries(appdummy4
    PRIVATE Qt6::Quick
)

include(GNUInstallDirs)
install(TARGETS appdummy4
    BUNDLE DESTINATION .
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)
