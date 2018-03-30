macro (add_sources)
    file (RELATIVE_PATH _relPath "${CMAKE_SOURCE_DIR}" "${CMAKE_CURRENT_SOURCE_DIR}")
    foreach (_src ${ARGN})
        if (_relPath)
            list (APPEND SRCS "${_relPath}/${_src}")
        else()
            list (APPEND SRCS "${_src}")
        endif()
    endforeach()
    if (_relPath) # propagate SRCS to parent directory
        set (SRCS ${SRCS} PARENT_SCOPE)
    endif()
endmacro()

project(dtest)

cmake_minimum_required(VERSION 2.8.4)

find_package(OpenCV REQUIRED)


SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -O2 ")

include_directories(${OPENCV_INCLUDE_DIRS} /home/star/library/dlib-19.2/)

LINK_DIRECTORIES(/home/star/library/dlib-19.2/build/dlib/libdlib.so)

add_subdirectory(H264_camera)

#add_executable(wifi_tx ${SRCS})

ADD_LIBRARY(wifi_tx SHARED ${SRCS})

target_link_libraries(wifi_tx ${OpenCV_LIBS} )

