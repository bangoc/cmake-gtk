project(demo_jrb
        LANGUAGES C)

cmake_minimum_required(VERSION 2.6)

find_package(PkgConfig REQUIRED)
pkg_check_modules(GTK3 REQUIRED gtk+-3.0)

include_directories(${GTK3_INCLUDE_DIRS})
link_directories(${GTK3_LIBRARY_DIRS})

add_definitions(${GTK3_CFLAGS_OTHER} -rdynamic)

message(STATUS "Include: ${GTK3_INCLUDE_DIRS}\n LIB_DIR: ${GTK3_LIBRARY_DIRS} \n CFLAGS_OTHERS: ${GTK3_CFLAGS_OTHER} \n LIBS: ${GTK3_LIBRARIES}")

add_executable(textview textview.c)
target_link_libraries(textview ${GTK3_LIBRARIES})

add_executable(power2 power2.c)
add_executable(power2_gui power2_gui.c)
target_link_libraries(power2_gui ${GTK3_LIBRARIES})
add_executable(power2_gui_builder power2_gui_builder.c)
target_link_libraries(power2_gui_builder ${GTK3_LIBRARIES})