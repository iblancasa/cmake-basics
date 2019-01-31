# Compile a C "hello world" application

We are going to learn the basics.

## How to compile a basic example

For CMake we need two steps:

1. Call CMake to generate the build system
2. Call the native tool to compile the applications

### Generating the build system

This directory looks like this:

```bash
    |-- CMakeLists.txt
    |-- README.md
    |-- myapp.c
```

You need to create a directory called ``build``. And move into it:

```bash
    mkdir build
    cd build
```

Then, you need to call CMake:

```bash
    cmake ..
```

Once you have run CMake, you will find a number of new files in your
build directory (the list of generated files will depend on the specific
CMake Generator). To build the example, run CMake as follows:

```bash
   cmake --build .
```

**Note**: if you are using a multi-configuration generator, such as
Visual Studio solutions, you can specify the configuration mode to build
as follows:

```bash
   cmake --build . --configuration Release|Debug
```

Alternatively, you can use directly the generated infrastructure (e.g.,
Makefiles or Visual Studio Solutions) to build the example. If you
generated Makefiles in the configuration process, run make to build the
example. Likewise, if you generated a Visual Studio solution, open the
solution and follow the regular build process.

## Configuring Build Type and Generator

By default, CMake will generate build files using the most common
generator for your host platform (e.g., Makefiles on Unix-like systems
and Visual Studio solution on Windows). You can use the following CMake
variables to modify the default behavior:

- ``-DCMAKE_BUILD_TYPE`` – specifies the build mode. Valid values are Release and Debug. See the [CMake documentation for more details (Optional)](https://cmake.org/cmake/help/latest/variable/CMAKE_BUILD_TYPE.html)
- ``-DBUILD_SHARED_LIBS`` – specifies the link mode. Valid values are ``ON`` for dynamic linking and ``OFF`` for static linking. [See CMake documentation for more details. (Optional)](https://cmake.org/cmake/help/latest/variable/BUILD_SHARED_LIBS.html)
- ``-G`` – CMake generator. The generator is the native build system to use build the source code. [All the valid values are described described in the CMake documentation CMake Generators Section](https://cmake.org/cmake/help/v3.13/manual/cmake-generators.7.html)

For example, to build a example in Debug/Static mode run CMake as
follows:

```bash
   cmake -DCMAKE_BUILD_TYPE=Debug -DBUILD_SHARED_LIBS=ON ..
```
