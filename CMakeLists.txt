cmake_minimum_required(VERSION 3.22)

project(libmodule)

include("shared.cmake")

set(LIBMODULE_DIR "./")
file(GLOB_RECURSE LIBMODULE_SOURCES "${LIBMODULE_DIR}/module.cpp" "${LIBMODULE_DIR}/*.h")
if(WIN32)
	list(APPEND LIBMODULE_SOURCES "${LIBMODULE_DIR}/module_windows.cpp")
else()
	list(APPEND LIBMODULE_SOURCES "${LIBMODULE_DIR}/module_linux.cpp")
endif()

add_library(${PROJECT_NAME} STATIC ${LIBMODULE_SOURCES})

set_target_properties(${PROJECT_NAME} PROPERTIES PREFIX "")
