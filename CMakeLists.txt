# cmake_minimum_required(VERSION 3.28)
# project(CMakeSFMLProject LANGUAGES CXX)

# option(BUILD_SHARED_LIBS "Build shared libraries" OFF)

# include(FetchContent)
# FetchContent_Declare(SFML
#     GIT_REPOSITORY https://github.com/SFML/SFML.git
#     GIT_TAG 2.6.x
# )
# FetchContent_MakeAvailable(SFML)

# FetchContent_Declare(
#   imgui
#   GIT_REPOSITORY https://github.com/ocornut/imgui
#   GIT_TAG v1.91.3
# )
# FetchContent_MakeAvailable(imgui)

# FetchContent_Declare(
#   imgui-sfml
#   GIT_REPOSITORY https://github.com/SFML/imgui-sfml
#   GIT_TAG v2.5
# )
# message(STATUS "Fetching ImGui-SFML...")

# set(IMGUI_DIR ${imgui_SOURCE_DIR})
# set(IMGUI_SFML_FIND_SFML OFF)
# set(IMGUI_SFML_IMGUI_DEMO ON)

# FetchContent_MakeAvailable(imgui-sfml)

# # add_subdirectory(src/tetris)

cmake_minimum_required(VERSION 3.28)
project(CMakeSFMLProject LANGUAGES CXX)

option(BUILD_SHARED_LIBS "Build shared libraries" OFF)

include(FetchContent)

FetchContent_Declare(SFML
    GIT_REPOSITORY https://github.com/SFML/SFML.git
    GIT_TAG 2.6.x
    GIT_SHALLOW ON
    EXCLUDE_FROM_ALL
    SYSTEM)
FetchContent_MakeAvailable(SFML)

FetchContent_Declare(ImGui
    GIT_REPOSITORY https://github.com/ocornut/imgui
    GIT_TAG v1.89.9
    GIT_SHALLOW ON
    EXCLUDE_FROM_ALL
    SYSTEM)
FetchContent_MakeAvailable(ImGui)
FetchContent_GetProperties(ImGui SOURCE_DIR IMGUI_DIR)

set(IMGUI_SFML_FIND_SFML OFF)
FetchContent_Declare(ImGui-SFML
    GIT_REPOSITORY https://github.com/SFML/imgui-sfml
    GIT_TAG 2.6.x
    GIT_SHALLOW ON
    EXCLUDE_FROM_ALL
    SYSTEM)
FetchContent_MakeAvailable(ImGui-SFML)

add_subdirectory(src/COMP4300_A1)