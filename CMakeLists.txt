cmake_minimum_required(VERSION 3.12)

project(Hello C)
include_directories(include)
# set(CMAKE_C_COMPILER   "D:/CustomSoftware/windows/Scoop/apps/msys2/current/mingw64/bin/gcc.exe")
# set(CMAKE_C_COMPILER   "D:\CustomSoftware\windows\Scoop\apps\mingw\current\bin\g++.exe)
add_executable(${PROJECT_NAME} src/Hello.c src/Zero.c)

# build(core): use SOURCE var to replace src
# aux_source_directory(src SOURCE)
# add_executable(${PROJECT_NAME} ${SOURCE})