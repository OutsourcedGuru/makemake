# makemake
A shell script suitable for generating a C++ `cmake`-compatible **CMakeLists.txt** file which then creates a **Makefile** for the `make` command

## Overview
If you're attempting to use the command line tools to build C++ files for ANSI-compatible purposes, you'll find that there are a number of steps involved.

1. In order to run the `make` command, you first need a `Makefile` in the project folder which describes what to build. Researching, you see that `cmake` shoud do this for you...
2. In order to create a `Makefile`, `cmake` first wants you to create a `CMakeList.txt` in the project folder. But now you'd need to research that format.

## What this script does
This script is meant to scaffold the current folder so that it's `make`-ready for simple C++ projects.

### Assumptions
* All `*.cpp` files are compiled together to create the executable
* The name of the executable is the lowercase version of the project folder's name itself (and the project name doesn't include any space characters)
* Your system runs shell scripts
* You have `make` and `cmake` in your path

## How to use
Place the `makemake` script somewhere in your PATH. I put mine in `~/local/scripts` which is in my path. Make sure that the script is marked so that it can execute: `chmod a+x makemake`

Finally, in the project folder itself, run `makemake`.

```
$ makemake
Determining project name... elvis
Reviewing .cpp files in current directory... main.cpp
Generating Makefile in current directory...
-- The C compiler identification is AppleClang 10.0.0.10001044
-- The CXX compiler identification is AppleClang 10.0.0.10001044
-- Check for working C compiler: /Library/Developer/CommandLineTools/usr/bin/cc
-- Check for working C compiler: /Library/Developer/CommandLineTools/usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /Library/Developer/CommandLineTools/usr/bin/c++
-- Check for working CXX compiler: /Library/Developer/CommandLineTools/usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done
-- Generating done
-- Build files have been written to: /Users/me/sites/Cplusplus/Elvis/Elvis
Making project...
Scanning dependencies of target elvis
[ 50%] Building CXX object CMakeFiles/elvis.dir/main.cpp.o
[100%] Linking CXX executable elvis
[100%] Built target elvis
```

## What it does
1. Generates a `CMakeLists.txt` file in the current directory
2. Runs `cmake . -G"Unix Makefiles"` in the current directory
3. Runs `make` in the current directory

## What's next?
Assuming that the executable works, the standard workflow then is simply:

1. Edit a `*.cpp` file, saving it
2. Run `make` in the project folder

|Description|Version|Author|Last Update|
|:---|:---|:---|:---|
|makemake|v1.0.1|OutsourcedGuru|December 30, 2018|