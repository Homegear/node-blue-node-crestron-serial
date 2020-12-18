cmake_minimum_required(VERSION 3.16)
project(crestron_serial)

set(CMAKE_CXX_STANDARD 14)

include_directories(.)
include_directories(crestron-serial-in)
include_directories(crestron-serial-out)
include_directories(crestron-serial-port)

add_library(crestron-serial-in SHARED crestron-serial-in/Factory.cpp
        crestron-serial-in/Factory.h
        crestron-serial-in/CrestronSerialIn.cpp
        crestron-serial-in/CrestronSerialIn.h)

add_library(crestron-serial-out SHARED crestron-serial-out/Factory.cpp
        crestron-serial-out/Factory.h
        crestron-serial-out/CrestronSerialOut.cpp
        crestron-serial-out/CrestronSerialOut.h)

add_library(crestron-serial-port SHARED crestron-serial-port/Factory.cpp
        crestron-serial-port/Factory.h
        crestron-serial-port/CrestronSerialPort.cpp
        crestron-serial-port/CrestronSerialPort.h
        crestron-serial-port/SerialReaderWriter.cpp
        crestron-serial-port/SerialReaderWriter.h)

add_custom_command(TARGET crestron-serial-in POST_BUILD COMMAND mv ARGS libcrestron-serial-in.so ../crestron-serial-in.so)
add_custom_command(TARGET crestron-serial-out POST_BUILD COMMAND mv ARGS libcrestron-serial-out.so ../crestron-serial-out.so)
add_custom_command(TARGET crestron-serial-port POST_BUILD COMMAND mv ARGS libcrestron-serial-port.so ../crestron-serial-port.so)