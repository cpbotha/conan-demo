project(sfmltest)
cmake_minimum_required(VERSION 3.5.2)

# pull in the generated conan cmake
include(conanbuildinfo.cmake)
conan_basic_setup()

add_executable(sfmltest sfmltest.cpp)
target_link_libraries(sfmltest ${CONAN_LIBS}) # note the conan libs over here

add_custom_command(TARGET sfmltest POST_BUILD
  COMMAND ${CMAKE_COMMAND} -E copy_directory
  "${PROJECT_SOURCE_DIR}/shaders/"
  $<TARGET_FILE_DIR:sfmltest>)

