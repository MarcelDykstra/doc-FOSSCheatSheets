# Build — Cheat Sheet

## C/C++ Build Commands

```
> gcc <src> -o <obj>       # C/C++ compile <src> to <obj>.
> gcc -g <src> -o <obj>    # C/C++ compile <src> to <obj> adding debug symbols.
> make                     # Compile and link source code according to "Makefile".
> make -j <cores>          # Compile and link source code according to "Makefile", using <cores> amount of CPU-cores.
> pkg-config --list-all                      # Output installed libraries.
> pkg-config --cflags <library>              # GCC compile flags for <library>.
> pkg-config --libs <library>                # GCC linker flags for <library>.
> objdump --syms <executable|obj.file>...    # Show debug symbol table inside executable <executable> or object file <obj.file> or multiple <executable|obj.file>.
> ldd <executable|obj.file>...               # Show shared object dependencies of executable <executable> or object file <obj.file> or multiple <executable|obj.file>.
> ldconfig -v                                # Scan en cache dynamic linker run-time bindings, with verbose information.
> ldconfig -p                                # Print the list of dynamic linker bindings currently stored in cache.
```

[![FOSS Cheat Sheets — License](https://img.shields.io/badge/LICENSE-CC0--1.0-blue?style=for-the-badge&logo=creativecommons&logoColor=white)](LICENSE.md)
