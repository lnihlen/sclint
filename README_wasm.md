# WASM Build Guide

## macOS Prerequisites

Homebrew recently added wasmtime, the runtime container:

`brew install wasmtime`

Need to install a new version of the wasi SDK from:

https://github.com/WebAssembly/wasi-sdk/releases

You will want to use curl to download the precompiled binaries, if you use a web browser the binaries will be marked as 
tainted and macOS won't run them.

```
curl -L https://github.com/WebAssembly/wasi-sdk/releases/download/wasi-sdk-16/wasi-sdk-16.0-macos.tar.gz \
     -o wasi-sdk-16.0-macos.tar.gz
```

Also need the wasmtime python interface:

`pip3 install wasmtime`



Configuring

```
cmake -GNinja -DWASI_SDK_PREFIX=${WASI_SDK} \
              -DCMAKE_TOOLCHAIN_FILE=${WASI_SDK}/share/cmake/wasi-sdk.cmake \
              -DCMAKE_MODULE_PATH=cmake
              -DWASM=On ..
```