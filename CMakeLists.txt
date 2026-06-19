cmake_minimum_required(VERSION 3.16)

if (DEFINED ESP_PLATFORM)
  # idf component
  idf_component_register(
      SRC_DIRS src/lib
      INCLUDE_DIRS src src/lib
  )

else()

  # set the project name
  project(codec-shine)

  # lots of warnings and all warnings as errors
  ## add_compile_options(-Wall -Wextra )
  set(CMAKE_CXX_STANDARD 17)

  file(GLOB_RECURSE SRC_LIST_C CONFIGURE_DEPENDS  "${PROJECT_SOURCE_DIR}/src/lib/*.c" )

  # define libraries
  add_library (codec-shine ${SRC_LIST_C} )

  # define location for header files
  target_include_directories(codec-shine PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/src ${CMAKE_CURRENT_SOURCE_DIR}/src/lib)

endif()