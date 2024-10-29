cmake_minimum_required(VERSION 3.10)

project(NatNetLinux)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)
add_library(NatNetLibs SHARED 
    include/NatNetCAPI.h 
    include/NatNetClient.h 
    include/NatNetRepeater.h 
    include/NatNetRequests.h 
    include/NatNetTypes.h
)
set_target_properties(NatNetLibs PROPERTIES LINKER_LANGUAGE CXX)


add_executable(${PROJECT_NAME} NatNetLinux.cpp)

target_link_directories(${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/lib)
target_link_libraries( ${PROJECT_NAME} NatNetLibs -lNatNet)
