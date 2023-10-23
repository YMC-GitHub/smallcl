## in win - mingw and cmake installing
- [x] install mingw and add it to PATH
```powershell
# mingw or msys2
# scoop install mingw
scoop install msys2

```

- [x] install cmake and add it to PATH
```powershell
scoop install cmake
```

- [x] install vscode and add it to PATH


## in vscode - c/c++ setting 
- prepare : mingw,cmake
```powershell
code --install-extension ms-vscode.cpptools-extension-pack
code --install-extension franneck94.c-cpp-runner
code --install-extension amiralizadeh9480.cpp-helper
code --install-extension ajshort.include-autocomplete
```
[refer: ext installing and choose build tools in vscode](https://www.bilibili.com/video/BV1ss4y1h7c5)


## in vscode - code clang of hello world 
- [x] add Hello.c

- [x] add CMakeList.txt


[hello world of clang in vscode](https://www.bilibili.com/video/BV1mq4y1b7xv)


##  in gcc - build *.c files to *.o files
- [x] in gcc - build *.c files to *.exe files
```powershell
# build:
gcc .\Hello.c -o Hello

# run:
# .\Hello.exe
```

- [x] in gcc - build *.c files to *.o
```powershell
gcc .\Hello.c -o Hello
```


- [x] clean output files of gcc
```powershell
del *.exe -recurse
```


## in cmake - build *.c files to *.o using msvc
- [x] add CMakeLists.txt

- [x] clean build files of cmake using msvc
```powershell
# del build files:
del *vcxproj* -recurse -force;del CMakeFiles -recurse -force;del *.sln -recurse -force;del CMakeCache.txt -recurse -force;del *.cmake -recurse -force;

# del *.exe -recurse -force;
```

- [x] clean build files of cmake using cmake
- if having using cmake
```powershell
del build/* -recurse -force;
```

- [x] build
```powershell
cmake .

# clean console:
# cls
```

##  in cmake - build *.c files to *.o using mingw
- [x] add CMakeLists.txt

- [x] clean build files of cmake using mingw
```powershell
del build/* -recurse -force;
```

- [x] tell vscode using mingw 
- in vscode , `ctrl + shift + p -> cmake:config -> ...`

it Executing command:
```
D:\CustomSoftware\windows\Scoop\shims\cmake.EXE --no-warn-unused-cli -DCMAKE_BUILD_TYPE:STRING=Debug -DCMAKE_TOOLCHAIN_FILE:STRING=D:\src\vcpkg\scripts\buildsystems\vcpkg.cmake -DVCPKG_TARGET_TRIPLET:STRING=x64-windows -DCMAKE_EXPORT_COMPILE_COMMANDS:BOOL=TRUE -DCMAKE_C_COMPILER:FILEPATH=D:\CustomSoftware\windows\Scoop\apps\mingw\current\bin\gcc.exe -DCMAKE_CXX_COMPILER:FILEPATH=D:\CustomSoftware\windows\Scoop\apps\mingw\current\bin\g++.exe -SD:/code/cpp/smallcl -Bd:/code/cpp/smallcl/build -G "MinGW Makefiles"
```

- [x] in vscode - in powershell terminal - build
```powershell
# config,build
# workflow: cmake -> makefile -> make
cd build;cmake ..;mingw32-make;
```

- [x] in vscode - in powershell terminal - run *.exe files

```powershell
# run
# done: run in powershell
.\Hello.exe

# done: run in cmd.exe in poweshell
# cmd.exe /c Hello


# .\build\Hello.exe
# cmd.exe /c build/Hello
```
- [x] fix `The C compiler identification is unknown`
- why:
```
[cmake] -- The C compiler identification is unknown
[cmake] CMake Error at CMakeLists.txt:3 (project):
[cmake]   The CMAKE_C_COMPILER:
[cmake] 
[cmake]     D:/CustomSoftware/windows/Scoop/apps/mingw/current/bin/gcc.exe
[cmake] 
[cmake]   is not a full path to an existing compiler tool.
[cmake] 
[cmake]   Tell CMake where to find the compiler by setting either the environment
[cmake]   variable "CC" or the CMake cache entry CMAKE_C_COMPILER to the full path to
[cmake]   the compiler, or to the compiler name if it is in the PATH.
```
- solution:
    - uc 1 - ensure mingw  installing and add it to PATH, eg. `scoop install mingw`
    - uc 2 - set CMAKE_C_COMPILER in CMakeLists.txt, eg. `(todo)` 
    - uc 3 - set CC in environment variable, eg. `(todo)` 


- refers:
```powershell
# get gcc location:
(gcm gcc).Source

# make sure mingw is install:
# dir (gcm gcc).Source

# CC,CMAKE_C_COMPILER,PATH
# https://cloud.tencent.com/developer/ask/sof/254330
# https://cloud.tencent.com/developer/ask/sof/590143
# https://blog.csdn.net/chengxiaili/article/details/132077417
# uc 1.
# set(CMAKE_C_COMPILER ${CROSS_COMPILE}gcc)
# uc 2.
# cmake -D CMAKE_C_COMPILER=xxx-gcc -D CMAKE_CXX_COMPILER==xxx-g++ .
```

[code clang of hello world - build *.c files to *.o using cmake](https://www.bilibili.com/video/BV1mq4y1b7xv)

## in vscode -  debug *.c files 

- [x] uc 1 - the base simple for one *.c files
- open xx.c file 
- add debug point 
- f5
- select gcc
- open teminal in vscode
- control debug
note:  vscode will auto gen : .vscode\tasks.json

- [x] uc 2 - the base some *.c files
- edit vscode/tasks.json

- [x] uc 3 - the base some *.c files
- edit CMakeLists.txt
- edit vscode/tasks.json
- edit vscode/launch.json


## design project dirs
- [x] add dirs
```powershell
$null=mkdir -p include;$null=mkdir -p src;
```

- [x] mov files
```powershell
mv *.h include;
mv *.c src;
```

## *.dll files - list function name
- in vs 2017 dev tool: (C:\Program Files (x86)\Microsoft Visual Studio\2017\BuildTools>)
```batch
dumpbin /exports "G:\biansuchilun0.46\GearNtKe.dll"
```
[refer: list function name in some *.dll files ](https://blog.csdn.net/qq_39220334/article/details/122394610)

## *.dll files - GearNtKe.dll - function list

```batch
dumpbin /exports "G:\biansuchilun0.46\GearNtKe.dll"
```
- AddProcess  -- 
- GetSpeed --
- SetSpeed -- 
- OldSetTimer
- UnIntercept --
```
File Type: DLL

  Section contains the following exports for GearNtKe.dll

    00000000 characteristics
    4965A58D time date stamp Thu Jan  8 15:04:45 2009
        0.00 version
           1 ordinal base
           5 number of functions
           5 number of names

    ordinal hint RVA      name

          1    0 00001520 AddProcess
          2    1 00001580 GetSpeed
          3    2 00001110 OldSetTimer
          4    3 000017B0 SetSpeed
          5    4 000016D0 UnIntercept

  Summary

        4000 .data
        8000 .rdata
        2000 .reloc
        1000 .rsrc
        1000 .sdata
       12000 .text
```

## *.dll files - hook.dll - function list
```batch
dumpbin /exports "G:\biansuchilun0.46\Hook.dll"
```

```
File Type: DLL

  Section contains the following exports for Hook.dll

    00000000 characteristics
    44C48036 time date stamp Mon Jul 24 16:09:26 2006
        0.00 version
           1 ordinal base
           9 number of functions
           9 number of names

    ordinal hint RVA      name

          1    0 00001170 ??0CHook@@QAE@XZ
          2    1 00001000 ??4CHook@@QAEAAV0@ABV0@@Z
          3    2 000010F0 SetHook
          4    3 00001120 SetHotKey
          5    4 00001160 SetMainWnd
          6    5 00001110 UnHook
          7    6 000011E0 UnloadGear
          8    7 000010E0 fnHook
          9    8 0000AA70 nHook

  Summary

        4000 .data
        1000 .rdata
        1000 .reloc
        1000 .sdata
        5000 .text
```

## *.exe files - get *.dll file of dependency 
- in vs 2017 dev tool: (C:\Program Files (x86)\Microsoft Visual Studio\2017\BuildTools>)
```cmd
dumpbin.exe /dependents "G:\biansuchilun0.46\GearNT.exe"
```

```
  Image has the following dependencies:

    kernel32.dll
    user32.dll
    advapi32.dll
    oleaut32.dll
    kernel32.dll
    advapi32.dll
    kernel32.dll
    version.dll
    gdi32.dll
    user32.dll
    kernel32.dll
    oleaut32.dll
    comctl32.dll
    imm32.dll
    winspool.drv
    shell32.dll
    comdlg32.dll
    GearNtKe.dll
    hook.dll
```
[Windows Ways to View Exe Dependent DLLs](https://zhuanlan.zhihu.com/p/395557318)

## *.dll files - make and call custom *.dll file - hello world 
- [x] edit source file `hicl.c`
```c
#include <stdio.h>
double lagtime(double p[],double Q[],int tm,int x,int y)
{
    double lag;
    //降雨为时段降雨，求矩形的形心横坐标
    double parea=0;
    double pxs[x];//各时段降雨形心横坐标
    double paxsum;
    double qarea=0;   
    double qxs[y];
    double qaxsum=0;//面积乘以

    for(int i=0;i<x;i++){
        parea+=p[i];
        pxs[i]=(2*i+1.0)/2;
        paxsum+=p[i]*pxs[i];
    }
    px=;
    for(int i=0;i<y;i++){
        qarea+=Q[i];
        qxs[i]=(2*i+1.0)/2;//第一个时段
        qaxsum+=Q[i]*qxs[i];
    }
    lag=(qaxsum/qarea-paxsum/parea)*tm;
    return lag;
}

```

- [x] add header file `hicl.h`, define functions in header file
```h
#include <stdio.h>
double lagtime(double p[],double Q[],int tm,int x,int y);
```

- [x] in gcc - make dynamic library dll
```bash
# gen *.o files from *.c files
gcc -c hicl.c -o hicl.o

# gen *.dll files from *.o files
gcc hicl.o -o libhicl.dll -shared
```

- [x] in clang - call dynamic libraries
- in `main.c`
```c
#include <stdio.h>
#include "hicl.h"
int main()
{
    double pp[]={1.8,10.3,14.7,3.4,1.6 };
    int cal_tm=6;
	double QQ[] = { 0,0,230,1120,1970,1340,843,600,440,320,230,180,140,110,80,50,40,20,0 };
    int x = sizeof(pp) / sizeof(pp[0]);
	int y = sizeof(QQ) / sizeof(QQ[0]);
    double lagtm=lagtime(pp,QQ,cal_tm,x,y);
    printf("lagtime is：%f\n",lagtm);
    return 0;
}

```

- [x] in gcc - build *.c files to *.exe files
```bash
# gen *.o files from *.c files
gcc -c main.c -o main.o

# gen *.exe files from *.o files
gcc main.o -L. -llibhicl -o main.exe
```

- [x] run *.exe files in bash
```bash
./main.exe
```

[refer: 1 in c++ - make and call custom *.dll file ](https://learn.microsoft.com/zh-cn/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp?view=msvc-170)

[refer: 2 in c++ - make and call custom *.dll file](https://zhuanlan.zhihu.com/p/490440768)

[refer: 3 in c++ - in vscode - in mingw - make and call custom *.dll file](https://blog.csdn.net/weixin_46777141/article/details/125907453)

[refer: 4 ](https://blog.csdn.net/qq_53744721/article/details/122902857)

- [x] in makefile - build *.c files to *.dll files
- makefile tpl for building *.dll
```
BIN=./bin
OBJ=./obj
INC=./include
SRC=./src

SRCS=$(wildcard $(SRC)/*.c)
OBJS=$(patsubst %.c,$(OBJ)/%.o,$(notdir $(SRCS)))

TARGET=main
TARGET_PATH=$(BIN)/$(TARGET)

CC=gcc
CFLAGS=-g -Wall -I$(INC)

LIB_PATH=-L$(BIN)
LIB_FLAGS=-lmymath

$(TARGET_PATH):$(OBJS)
	$(CC) $^ $(LIB_PATH) $(LIB_FLAGS) -o $@

$(OBJ)/%.o:$(SRC)/%.c
	$(CC) -c $(CFLAGS) $^ -o $@

.PHONY: clean

clean:
	del /Q /F obj

```

- [x] in makefile - build *.c files to *.lib files
- makefile tpl for building *.lib
```
BIN=./bin
OBJ=./obj
INC=./include
SRC=./src
LIB=./lib

SRCS=$(wildcard $(SRC)/*.c)
OBJS=$(patsubst %.c,$(OBJ)/%.o,$(notdir $(SRCS)))

TARGET=main
TARGET_PATH=$(BIN)/$(TARGET)

CC=gcc
CFLAGS=-g -Wall -I$(INC)

LIB_PATH=-L $(LIB)
LIB_FLAGS=-l libzzz

$(TARGET_PATH):$(OBJS)
	$(CC) $^ $(LIB_PATH) $(LIB_FLAGS) -o $@

$(OBJ)/%.o:$(SRC)/%.c
	$(CC) -c $(CFLAGS) $^ -o $@

.PHONY: clean

clean:
	del /Q /F obj

```

- [x] in makefile - build *.c files to *.lib and *.dll files
```
BIN=./bin
OBJ=./obj
INC=./include
SRC=./src
LIB=./lib

SRCS=$(wildcard $(SRC)/*.c)
OBJS=$(patsubst %.c,$(OBJ)/%.o,$(notdir $(SRCS)))

TARGET=main
TARGET_PATH=$(BIN)/$(TARGET)

CC=gcc
CFLAGS=-g -Wall -I$(INC)

LIB_PATH=-L$(BIN) -L$(LIB)
LIB_FLAGS=-lmathdm -llibmathas 

$(TARGET_PATH):$(OBJS)
	$(CC) $^ $(LIB_PATH) $(LIB_FLAGS) -o $@

$(OBJ)/%.o:$(SRC)/%.c
	$(CC) -c $(CFLAGS) $^ -o $@

.PHONY: clean
clean:
	del /Q /F obj

```

## *.dll file - in cmake - make and call 
- cmkae -> makefiles -> gcc -> *.dll
