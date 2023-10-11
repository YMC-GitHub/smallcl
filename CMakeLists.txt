cmake_minimum_required(VERSION 3.12)

project(Hello C)
# set(CMAKE_C_COMPILER   "D:/CustomSoftware/windows/Scoop/apps/msys2/current/mingw64/bin/gcc.exe")
# set(CMAKE_C_COMPILER   "D:\CustomSoftware\windows\Scoop\apps\mingw\current\bin\g++.exe)
add_executable(${PROJECT_NAME} Hello.c Zero.c)