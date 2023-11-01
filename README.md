![build](https://github.com/mattiasgustavsson/template_project/actions/workflows/main.yml/badge.svg)

# template_project
Basic setup for building something with app.h on Windows/Linux/Mac/Web

## Building

No build system is used, simply call the compiler from the commandline.


### Windows

From a Visual Studio Developer Command Prompt, do:
```
  cl source\main.c
```  

Alternatively, you can use Tiny C Compiler:
```
tcc\tcc source\main.c
```
You can download tcc here: [tiny-c-compiler](https://github.com/mattiasgustavsson/template_project/releases/tag/tiny-c-compiler) for either 32 or 64 bit Windows. Unzip it so that the `tcc` folder in the zip file is at your repository root.

### Mac

```
  clang source/main.c `sdl2-config --libs --cflags` -lGLEW -framework OpenGL -lpthread
```

SDL2 and GLEW are required - if you don't have them installed you can do so with Homebrew by running
```
  brew install sdl2 glew  
```


### Linux

```
  gcc source/main.c `sdl2-config --libs --cflags` -lGLEW -lGL -lm -lpthread
```

SDL2 and GLEW are required - if you don't have them installed you can do so on Ubuntu (or wherever `apt-get` is available) by running
```
  sudo apt-get install libsdl2-dev
  sudo apt-get install libglew-dev
```


### WebAssembly

Using WAjic:
```
  wasm\node wasm\wajicup.js source/main.c main.html
```
You can embed asset files in the process with the -embed parameter. 

A WebAssembly build environment is required. You can download it (for Windows) here: [wasm-build-tools-win](https://github.com/mattiasgustavsson/template_project/releases/download/wasm-build-tools/wasm-build-tools-win.zip).
Unzip it so that the `wasm` folder in the zip file is at your repository root.

The wasm build environment is a compact distribution of [node](https://nodejs.org/en/download/), [clang/wasm-ld](https://releases.llvm.org/download.html),
[WAjic](https://github.com/schellingb/wajic) and [wasm system libraries](https://github.com/emscripten-core/emscripten/tree/main/system).
