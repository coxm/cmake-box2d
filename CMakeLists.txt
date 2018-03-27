cmake_minimum_required(VERSION 3.7)

project(Box2D)


option(BUILD_SHARED_LIBS "Build shared libraries" ON)


if(NOT BOX2D_ROOT_DIR)
	message(FATAL_ERROR "Environment variable BOX2D_ROOT_DIR is not defined")
endif()


include_directories("${BOX2D_ROOT_DIR}/Box2D")


# Compiler flags.
list(APPEND MAIN_CXX_FLAGS
	-Werror -std=c++1z -Wall -Woverloaded-virtual
	-Wsign-promo -Wno-pmf-conversions -Wshadow
)
if(CMAKE_BUILD_TYPE MATCHES "Debug")
	list(APPEND MAIN_CXX_FLAGS -O0 -ggdb3)
	set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -O0 -ggdb3")
endif()


file(GLOB_RECURSE CPP_SOURCES "${BOX2D_ROOT_DIR}/Box2D/Box2D/**/*.cpp")


add_library(${PROJECT_NAME} ${CPP_SOURCES})
target_compile_options(${PROJECT_NAME} PUBLIC ${MAIN_CXX_FLAGS})
install(TARGETS ${PROJECT_NAME} LIBRARY DESTINATION lib)
