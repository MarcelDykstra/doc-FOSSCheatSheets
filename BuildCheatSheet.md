# Build — Cheat Sheet

## C/C++ Build Commands

```
> gcc <src> -o <obj>       # C/C++ compile <src> to <obj>.
> gcc -g <src> -o <obj>    # C/C++ compile <src> to <obj> adding debug symbols.
> make                     # Compile and link source code according to "Makefile".
> make -j <cores>          # Compile and link source code according to "Makefile", using <cores> amount of CPU-cores.
> pkg-config --list-all           # Output installed libraries.
> pkg-config --cflags <library>   # GCC compile flags for <library>.
> pkg-config --libs <library>     # GCC linker flags for <library>.
```

[![FOSS Cheat Sheets — License](https://img.shields.io/badge/LICENSE-CC0--1.0-blue?style=for-the-badge&logo=creativecommons&logoColor=white)](LICENSE.md)
