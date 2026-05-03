## Overview
This project is a simple 2D physics simulation of bouncing balls using a custom C-based library. The application provides an interactive window where users can observe the behavior of multiple balls as they collide and bounce off each other under the influence of gravity.

## Features
- Multiple bouncing balls
- Gravity effect
- Collision detection and response
- Cross-platform build support (Linux, Windows, WebAssembly)
- Debugging capabilities

## Project Structure
```
Gui_Balls_Physics/
├── README.md
├── LICENSE
├── .gitignore
├── src/
│   ├── Main.c
│   └── *.h
├── Makefile.linux
├── Makefile.windows
├── Makefile.wine
└── Makefile.web
```

### Prerequisites
- C/C++ Compiler and Debugger (GCC)
- Make utility
- Standard development tools
- X11 library for Linux builds (`libX11`)
- User32, GDI32, Winmm libraries for Windows builds (`mingw-w64`)

## Build & Run
### Linux
To build and run on Linux:

```sh
cd Gui_Balls_Physics
make -f Makefile.linux all
make -f Makefile.linux exe
```

### Windows
To build and run on Windows using MinGW:

```sh
cd Gui_Balls_Physics
make -f Makefile.windows all
make -f Makefile.windows exe
```

### WebAssembly (Emscripten)
To build for the web:

```sh
cd Gui_Balls_Physics
emcc -O0 -msimd128 -mavx2 -std=gnu17 -Wall -Wno-unused -Wshadow -Werror -Isrc -D_WEB -sINITIAL_MEMORY=169082880 src/*.c -o build/index.html -sUSE_SDL=0
# Serve the output using a local web server (emrun)
emrun --no_browser --port 8080 build/
```

### Debugging
To debug the application:

```sh
make -f Makefile.linux debug
```

or for Windows:

```sh
make -f Makefile.windows debug
```

This setup ensures that the project can be built and executed on multiple platforms, providing a versatile development environment.