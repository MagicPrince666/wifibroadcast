cmake_minimum_required (VERSION 2.6)

PROJECT(main)

INCLUDE_DIRECTORIES(. ./H264_camera)

ADD_SUBDIRECTORY( H264_camera )

ADD_DEFINITIONS(-O3 -g -W -Wall -std=gnu++11)


link_libraries(pcap rt pthread sodium)

add_executable(tx
        fec.c
        tx.cpp
        wifibroadcast.cpp
)

# link library in static mode
target_link_libraries(tx camera)
