# A Documented Simple Naive Surface Nets Implementation

## Overview

This repository implements the *Naive Surface Nets Algorithm* which is used to generate a triangular mesh that approximates a given isosurface defined by the level-set `{ x,y,z in R^3 | f(x,y,z)=isovalue }` of a scalar function `f: R^3 -> R`. The approximation's precision is bounded by a given voxel grid's resolution in which the isosurface to extract is contained. In the [main.cpp](./main.cpp) file, you can find an example use of the `surface_nets` function which generates a mesh of the unit circle `f(x,y,z) = sqrt(x*x + y*y + z*z) - 1.0` at the specified grid resolution. We add [libigl](https://github.com/libigl/libigl/) as submodule for visualization of the generated triangular meshes.

## Goals

This repository aims to provide a clear, simple and documented implementation of the naive surface nets algorithm that is (in my opinion) much needed. Most open source implementations are hard to read and poorly documented, assuming much prior knowledge from the readers or optimized at the expense of readability and simplicity. This repository's implementation assumes minimal prior knowledge of:
- scalar functions defined in 3d space and how a level-set of such functions defines a 2d surface embedded in 3d space
- basic data structures (arrays, vectors, dictionaries)
- the [shared vertex mesh data structure](http://www.enseignement.polytechnique.fr/informatique/INF562/Slides/MeshDataStructures.pdf)

The [surface_nets.cpp](./src/surface_nets.cpp) file contains thorough documentation of the surface nets implementation in the form of comments. I hope this will be of help to many for learning mesh generation algorithms.

## Dependencies

- [Eigen3](http://eigen.tuxfamily.org/index.php?title=Main_Page)
- [glfw](https://www.glfw.org/)
- [glad](https://glad.dav1d.de/)
- [libigl](https://github.com/libigl/libigl/)
- [Cmake](https://cmake.org/)
- C++14 compiler

The [CMakeLists.txt](./CMakeLists.txt) assumes that the Eigen, glfw and glad libraries are found by cmake `find_package` calls. Don't forget to clone the libigl submodule.

## Building

```
$ git clone --recurse-submodules https://github.com/Q-Minh/naive-surface-nets
$ cd naive-surface-nets
$ mkdir build
$ cd build
$ cmake .. -G <your build system generator> # -DCMAKE_TOOLCHAIN_FILE=<path to vcpkg>/scripts/buildsystems/vcpkg.cmake if you are using vcpkg
$ cmake --build .
```

## Helpful Documentation

- [Constrained Elastic Surface Nets](https://www.merl.com/publications/docs/TR99-24.pdf)
- ["Wenger, Rephael", Isosurfaces: Geometry, Topology, and Algorithms 1st edition, A K Peters/CRC Press, June 24 2013](https://www.amazon.ca/Isosurfaces-Geometry-Algorithms-Rephael-Wenger/dp/1466570970)
- [Mikola Lysenko's article](https://0fps.net/2012/07/12/smooth-voxel-terrain-part-2/)
- [Paul Bourke's Marching Cubes article](http://paulbourke.net/geometry/polygonise/)
- [Polygon Mesh Processing by Kobbelt, Botsch and Pauly](http://www.pmp-book.org/)