cmake_minimum_required(VERSION 3.4)                                    
 
project(ObjectPool VERSION 1.2 LANGUAGES CXX)

#add_compile_options(-std=c++11)

set(CMAKE_CXX_STANDARD 11) 
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_STANDARD_REQUIRED ON) 
set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS ON) 


if(NOT ENABLE_TRAVIS)
  find_package(GTest REQUIRED)
  message(STATUS "find_package ${ENABLE_TRAVIS}")
  include_directories(${GTEST_INCLUDE_DIRS})
endif()

add_executable(${PROJECT_NAME}_test object_pool_test.cpp )

target_link_libraries(${PROJECT_NAME}_test ${GTEST_BOTH_LIBRARIES})


enable_testing()
add_test(
  NAME google_test
  COMMAND $<TARGET_FILE:${PROJECT_NAME}_test>
  )