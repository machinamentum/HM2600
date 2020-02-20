# Atari 2600 Emulator in [Jiyu](https://github.com/machinamentum/jiyu)

This is by no means a comprehensive, cycle-accurate emulator.

There are far better techniques for building fast interpreters.. I have avoided using them here since the Atari 2600 does rely heavily on individual hardware chips being synchronized on the same system clocks (with the CPU and RIOT chip clocks being the TIA's clock divided by 3). There's also no `goto` support in Jiyu at the time of this project being developed, so I have opted to stick with a simple switch-statement for the interpreter step. An effort had been made to reduce code bloat across instructions that perform the same operation but use different addressing modes. Unfortunately, due to the 6502's instruction set having some irregularities, there is a little bit more bloat than I'd like, but the interpreter is still fairly concise.

## Build
A C compiler is required to compile the stb_truetype.h library. The build file, `build.jyu` will attempt to find the MSVC compiler, cl.exe, on Windows using Jon Blow's microsoft_craziness.h library. This may fail in some cases and with some versions of Visual Studio.

The emulator can be built simply by compiling the build file, `build.jyu`:

`jiyu build.jyu`

## Usage
Supported ROM formats are 2K and 4K. Larger ROM files require cart banking support that is currently not implemented.

There is currently no GUI for selecting a ROM to load. The emulator must be invoked via the command line:

`run_tree/a2600 rom_file_to_load.bin`

Currently, the arrow keys may be used for joystick input, spacebar may be used as the fire button, key-1 may be used for the Reset switch, and key2 for Select.
