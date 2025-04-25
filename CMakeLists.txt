# language: CMake

cmake_minimum_required(VERSION 3.25)

project(project)
include(.cmake/settings.cmake)

# MARK: Lesson folders
file(GLOB_RECURSE DIRS LIST_DIRECTORIES true ".")

string(REPLACE ";" "|" PREFIX "${LESSON_PREFIXES}")

foreach(DIR ${DIRS})
  if(IS_DIRECTORY ${DIR})
    if(${DIR} MATCHES "${PROJECT_NAME}/(${PREFIX})[^/]*$")
      add_subdirectory(${DIR})
    endif()
  endif()
endforeach()

# MARK: Library
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/${LIB_NAME})