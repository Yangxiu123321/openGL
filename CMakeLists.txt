cmake_minimum_required(VERSION 3.0)

# Project Name
set(PROJ_NAME openGL)
project(${PROJ_NAME})

set (LIB_DL dl)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -march=native -O3 -pthread -lglfw3 -lGL -lm -lXrandr -lXi -lX11 -lXxf86vm -lpthread -ldl -lXinerama -lXcursor")
#set(EXECUTABLE_OUTPUT_PATH ${CMAKE_SOURCE_DIR}/bin)

set (GLAD_PATH /home/action/code/openGL/glad/src)
# set (GLFW_LIB_PATH /home/action/code/openGL/glfw/build/src/libglfw3.a)

find_package(OpenGL REQUIRED)
find_package(glfw3 REQUIRED)

FILE(GLOB HEADER_LIST ${CMAKE_CURRENT_SOURCE_DIR}/src/*.h)
FILE(GLOB SOURCE_LIST ${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp ${CMAKE_CURRENT_SOURCE_DIR}/.c)

add_executable(${PROJ_NAME} ${SOURCE_LIST} ${HEADER_LIST})
set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT ${PROJ_NAME})

#3.head file path，头文件目录
INCLUDE_DIRECTORIES(
  
)

TARGET_LINK_LIBRARIES(${PROJECT_NAME} ${GLFW_LIB_PATH} ${LIB_DL} glfw)

