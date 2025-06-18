cmake_minimum_required(VERSION 3.20)
project(CGNS_Test)

#set(USE_TEST 1)

if(USE_TEST)
enable_testing()
endif()

#set(CMAKE_CONFIGURATION_TYPES "Debug;Release")
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

set(SOURCE_FILES 
    write_grid_unst.c)
add_executable(${PROJECT_NAME} ${SOURCE_FILES})

include_directories(
  ../../../Win/CGNS/v4.5.0/m_install/include
  ../../../Win/hdf5/v1.14.6/m_install/include
  ../../../Win/zlib/v1.3.1/install_release/include
)

target_link_directories(${PROJECT_NAME} PRIVATE
  ../../../Win/CGNS/v4.5.0/m_install/lib
  ../../../Win/hdf5/v1.14.6/m_install/lib
  ../../../Win/zlib/v1.3.1/install_release/lib
)

target_link_libraries(${PROJECT_NAME} PRIVATE cgns hdf5 zlib)