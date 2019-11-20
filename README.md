# Include-C-library-in-CmakeList
how to include a C library to a project with CmakeList.txt

this is a sample solution for  Unix (Linux, OS X) users , for those who have installed libusb (or nother) and don't find it included in the standard library

if you follow the logs of hombrew (or any other package manager), you will find the path that homebrew has chosen for the installation of the library on your Os

for my part, he added the library in "/ usr / local / Cellar / libusb",

well there is surely a way to add the library on the GCC standard library, but here I will show you an example of a cmakeList.txt file that you can use for your project to includ it on the project at least 

open a new project and this is what you need to put in your cmakelist.txt file

`
cmake_minimum_required(VERSION 3.15)
project(libusb)

set(CMAKE_CXX_STANDARD 14)
add_executable(libusb main.cpp)

INCLUDE_DIRECTORIES(/usr/local/Cellar/libusb/1.0.23/include)
LINK_DIRECTORIES(/usr/local/Cellar/libusb/1.0.23/lib)

file(GLOB LIBRARIES "/usr/local/Cellar/libusb/1.0.23/lib/*.dylib")
message("LIBRARIES = ${LIBRARIES}")

TARGET_LINK_LIBRARIES(libusb ${LIBRARIES})
`

restart your compilation and it should work

if you have an idea of how I could add it back to the library that my gcc uses, you can post the solution down, thank you
