Fleet uses CMake to generate massively parallel C++ projects for build
acceleration benchmarking.

# Quick start

    $ git clone https://github.com/benmcmorran/fleet.git
    $ cd fleet
    
The examples below create a library with 10,000 translation units (TUs) that have
no dependencies on each other.

To build sequentially run:

    $ cmake -DTU_COUNT=10000 -DPROJECT_TYPE=flat
    $ time cmake --build .

To build with parallelism of 100 using Ninja run:

    $ cmake -G Ninja -DTU_COUNT=10000 -DPROJECT_TYPE=flat -DCMAKE_BUILD_TYPE=Release
    $ time cmake --build . -- -j 100

# Usage

Specify `TU_COUNT` and `PROJECT_TYPE` as CMake variables during generation to
use Fleet. Currently `flat` is the only project type available. It will generate
a library where each TU consists of a single function that prints an identifier
to standard out.
