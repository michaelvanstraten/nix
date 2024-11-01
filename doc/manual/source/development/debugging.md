# Debugging Nix

This section shows how to build and debug Nix with debug symbols enabled.

## Building Nix with debug symbols

In the development shell, set the `mesonBuildType` environment variable to `debug` before configuring the build:

```console
[nix-shell]$ export mesonBuildType=debugoptimized
```

Then, proceed to build Nix as described in [Building Nix](./building.md).

## Debugging the Nix binary

Obtain your preferred debugger within the development shell:

```console
[nix-shell]$ nix-shell -p gdb
```

On macOS, use `lldb`:

```console
[nix-shell]$ nix-shell -p lldb
```

### Launching the debugger

To debug the Nix binary, run:

```console
[nix-shell]$ gdb --args ../outputs/out/bin/nix
```

On macOS, use `lldb`:

```console
[nix-shell]$ lldb -- ../outputs/out/bin/nix
```

### Using the debugger

Inside the debugger, you can set breakpoints, run the program, and inspect variables.

```gdb
(gdb) break main
(gdb) run <arguments>
```

Refer to the [GDB Documentation](https://www.gnu.org/software/gdb/documentation/) for comprehensive usage instructions.

On macOS, use `lldb`:

```lldb
(lldb) breakpoint set --name main
(lldb) process launch -- <arguments>
```

Refer to the [LLDB Tutorial](https://lldb.llvm.org/use/tutorial.html) for comprehensive usage instructions.
