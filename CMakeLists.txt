cmake_minimum_required(VERSION 3.15)

project(implot)

add_library(${PROJECT_NAME})
find_package(imgui REQUIRED)
target_link_libraries(${PROJECT_NAME} PUBLIC imgui::imgui)
target_sources(${PROJECT_NAME} PRIVATE
    implot.cpp
    implot_items.cpp
)

set_target_properties(${PROJECT_NAME} PROPERTIES PUBLIC_HEADER 
"implot.h;implot_internal.h;"
)

install(TARGETS ${PROJECT_NAME}
    RUNTIME DESTINATION ${CMAKE_INSTALL_LIBDIR}
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
    INCLUDES DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
    PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/implot/
)