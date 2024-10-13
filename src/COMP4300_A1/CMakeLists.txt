cmake_minimum_required(VERSION 3.28)
project(COMP4300_A1 LANGUAGES CXX)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/COMP4300_A1/bin)

add_executable(comp4300_a1 comp4300_a1.cpp)
target_link_libraries(comp4300_a1 PRIVATE sfml-graphics)
target_link_libraries(comp4300_a1 PRIVATE ImGui-SFML::ImGui-SFML)
target_compile_features(comp4300_a1 PRIVATE cxx_std_17)

if(WIN32)
    add_custom_command(
        TARGET comp4300_a1 
        COMMENT "Copy OpenAL DLL"
        PRE_BUILD COMMAND ${CMAKE_COMMAND} -E copy ${SFML_SOURCE_DIR}/extlibs/bin/$<IF:$<EQUAL:${CMAKE_SIZEOF_VOID_P},8>,x64,x86>/openal32.dll $<TARGET_FILE_DIR:comp4300_a1>
        VERBATIM)
endif()

# Copy fonts directory to the output directory
add_custom_command(
    TARGET comp4300_a1
    POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_directory
    ${CMAKE_CURRENT_SOURCE_DIR}/fonts
    $<TARGET_FILE_DIR:comp4300_a1>/fonts
    COMMENT "Copying fonts directory to output directory"
)

# Copy config.txt to the output directory
add_custom_command(
    TARGET comp4300_a1
    POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy
    ${CMAKE_CURRENT_SOURCE_DIR}/config.txt
    $<TARGET_FILE_DIR:comp4300_a1>
)