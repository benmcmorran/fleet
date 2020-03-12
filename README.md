Fleet uses CMake to generate massively parallel C++ projects for build
acceleration benchmarking.

# Quick start

    $ git clone https://github.com/benmcmorran/fleet.git
    $ mkdir fleet/out
    $ cmake -S fleet -B fleet/out -DTU_COUNT=10000 -DPROJECT_TYPE=flat
    $ time cmake --build fleet/out

This will create a library with 10,000 translation units (TUs) that have no
dependencies on each other.

# Usage

Specify `TU_COUNT` and `PROJECT_TYPE` as CMake variables during generation to
use Fleet. Currently `flat` is the only project type available. It will generate
a library where each TU consists of a single function that prints an identifier
to standard out.
