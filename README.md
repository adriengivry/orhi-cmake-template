# OpenRHI CMake Template

A template project to quickly get started with [OpenRHI](https://github.com/adriengivry/orhi), using [CMake](https://cmake.org) as the build system.

**Includes:**
- [glfw](https://github.com/glfw/glfw)
- [glm](https://github.com/g-truc/glm)
- [orhi](https://github.com/adriengivry/orhi)

## Getting Started
1. Download and install [CMake](https://cmake.org/download/)
2. Create a new repository based on this template
3. Clone your repository
4. Edit the following lines in `CMakeLists.txt`:
```cmake
project(my-project) # Replace with your project name

FetchContent_Declare(
    orhi
    GIT_REPOSITORY https://github.com/adriengivry/orhi.git
    GIT_TAG main # (optional) Replace with the version you want to use, e.g. v0.1.0
)
```
5. Generate projects:
```powershell
cmake ./
```
6. You're all set! Enjoy!
