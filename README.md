# ![xeus](http://quantstack.net/assets/images/xeus.svg)

[![Travis](https://travis-ci.org/QuantStack/xeus.svg?branch=master)](https://travis-ci.org/QuantStack/xeus)
[![AppVeyor](https://ci.appveyor.com/api/projects/status/5alkw5iiere4mox2?svg=true)](https://ci.appveyor.com/project/QuantStack/xeus)
[![Documentation Status](http://readthedocs.org/projects/xeus/badge/?version=latest)](https://xeus.readthedocs.io/en/latest/?badge=latest)

C++ implementation of the Jupyter Kernel protocol

## Introduction

`xeus` is a library meant to facilitate the implementation of kernels for Jupyter. It takes the
burden of implementing the Jupyter Kernel protocol so developers can focus on implementing the
interpreter part of the Kernel.

## Building and Installing from Source

`xeus` depends on the following libraries:

 - [`libzmq`](https://github.com/zeromq/libzmq) ^4.2.1, [`cppzmq`](https://github.com/zeromq/cppzmq), [`rapidjson`](https://github.com/miloyip/rapidjson) and [`cryptopp`](https://github.com/weidai11/cryptopp).

On Unix platforms, `xeus` also requires `libuuid`, which is available in all linux distributions (`uuid-dev` on Debian).

We have packaged all these dependencies for the conda package manager. The simplest way to install them with
conda is to run:

```bash
conda install cmake zeromq cppzmq rapidjson cryptopp -c conda-forge
```

On Unix platform, you will also need:

```bash
conda install libuuid -c conda-forge
```

Once you have installed the dependencies, you can build and install `xeus`:

```bash
cmake -D BUILD_EXAMPLES=ON -D CMAKE_BUILD_TYPE=Release
make
make install
```

If you need the `xeus` library only, you can omit the `BUILD_EXAMPLES` settings.

## Installing the Dependencies from Source

### libzmq

```bash
cmake -D WITH_PERF_TOOL=OFF -D ZMQ_BUILD_TESTS=OFF -D ENABLE_CPACK=OFF
-D CMAKE_BUILD_TYPE=Release
make
make install
```

### cppzmq

`cppzmq` is a header only library:

```bash
cmake -D CMAKE_BUILD_TYPE=Release
make install
```

### rapidjson

`rapidjson` is a header only library too, but requires some options to be set:

```bash
cmake -D RAPIDJSON_BUILD_DOC=OFF -D RAPIDJSON_BUILD_TESTS=OFF
-D RAPIDJSON_BUILD_EXAMPLES=OFF -D RAPIDJSON_HAS_STDSTRING=ON
-D CMAKE_BUILD_TYPE=Release
make install
```

### cryptopp

`cryptopp` must be built as a static library, the shared library build doest' work on
Windows.

```bash
cmake -D BUILD_SHARED=OFF -D BUILD_TESTING=OFF -D CMAKE_BUILD_TYPE=Release
make
make install
```

## License

We use a shared copyright model that enables all contributors to maintain the
copyright on their contributions.

This software is licensed under the BSD-3-Clause license. See the [LICENSE](LICENSE) file for details.
