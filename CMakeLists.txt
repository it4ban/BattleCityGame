cmake_minimum_required(VERSION 3.23)

project(BattleCity LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
set(GLFW_INSTALL OFF CACHE BOOL "" FORCE)

add_subdirectory(external/glfw)

add_executable(BattleCity
    src/main.cpp
)

target_link_libraries(BattleCity PRIVATE glfw)

if(APPLE)
    target_compile_definitions(BattleCity
        PRIVATE
            GL_SILENCE_DEPRECATION
    )

    target_link_libraries(BattleCity
        PRIVATE
            "-framework OpenGL"
    )
endif()
