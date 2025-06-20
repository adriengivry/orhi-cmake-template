cmake_minimum_required(VERSION 3.16)
project(my-project)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Source files
add_executable(${PROJECT_NAME} src/Main.cpp)

# Include files
target_include_directories(${PROJECT_NAME} 
    PRIVATE 
    ${CMAKE_CURRENT_SOURCE_DIR}/include
)

# Include FetchContent module
include(FetchContent)

# Fetch GLFW from GitHub
FetchContent_Declare(
    glfw
    GIT_REPOSITORY https://github.com/glfw/glfw.git
    GIT_TAG 3.4
)

# Fetch GLM from GitHub
FetchContent_Declare(
    glm
    GIT_REPOSITORY https://github.com/g-truc/glm.git
    GIT_TAG 1.0.1
)

# Fetch orhi from GitHub
FetchContent_Declare(
    orhi
    GIT_REPOSITORY https://github.com/adriengivry/orhi.git
    GIT_TAG main
)

# Configure GLFW options before making it available
set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)

# Select OpenGL as the graphics backend for OpenRHI
add_compile_definitions(ORHI_SELECT_OPENGL ORHI_COMPILE_OPENGL)

# Make dependencies available
FetchContent_MakeAvailable(glfw glm orhi)

# Link libraries
target_link_libraries(${PROJECT_NAME} 
    PRIVATE 
    glfw
    glm::glm
    orhi
)
