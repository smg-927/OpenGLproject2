cmake_minimum_required(VERSION 3.15)
project(OpenGLProject)

# C++ 표준 설정
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# 실행 파일 출력 위치 설정
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

# 소스 파일 및 헤더 파일 경로
set(SOURCES src/main.cpp external/glad/src/glad.c)
include_directories(external/glad/include external/glm external/glfw/include)

# OpenGL 라이브러리 찾기
find_package(OpenGL REQUIRED)

# GLFW 설정
add_subdirectory(external/glfw)

# 실행 파일 생성
add_executable(OpenGLApp ${SOURCES})

# 라이브러리 링크
target_link_libraries(OpenGLApp PRIVATE OpenGL::GL glfw)
