# Wii U PAC Extractor

Extracts the contents of `.bin` files that are PAC containers, as used by some
NDcube Wii U games. Developed and thinked for files from Mario Party 10.

The files are extracted raw: decompressed, in their original formats and with
their original folder tree. Nothing is converted.

## Requirements

- Windows
- Python 3 from [python.org](https://www.python.org/downloads/), with
  "Add Python to PATH" ticked (one time only)

## Usage

Drag a `.bin` file onto `Wii U PAC Extractor.exe`.

The extracted files are written next to the `.bin`, in a folder named
`<name>_extracted`.

You can also run it from the command line:

    python wiiu_pac_tool.py file.bin

Several files can be passed at once:

    python wiiu_pac_tool.py file1.bin file2.bin

## Important

`Wii U PAC Extractor.exe` is only a small launcher (source: `launcher.c`). It
calls `wiiu_pac_tool.py`, so both files must stay in the same folder.

## Example output

For a character package, the result looks like this:

    example_extracted/
    └── common/ch_base/npc/example/
        ├── example_body.gtx
        ├── example_killer.bnfm
        ├── example_killer.mcf
        └── mot/
            └── example_idle00.bnfmsa

Typical contents:

| Extension  | Contents                          |
|------------|-----------------------------------|
| `.gtx`     | Wii U (GX2) textures              |
| `.bnfm`    | 3D model                          |
| `.bnfmsa`  | Animations                        |
| `.mcf`     | Materials                         |

## Limitations

- Only PAC containers are supported. Any other `.bin` file is skipped with a
  message.
- Developed from a single sample file, so other files may fail.
- Files are extracted as they are. This tool does not convert textures, models
  or animations.

## Building the launcher

With MinGW-w64:

    x86_64-w64-mingw32-gcc -O2 -s -o "Wii U PAC Extractor.exe" launcher.c

## Disclaimer

This project is not affiliated with or endorsed by Nintendo or NDcube. It
contains no game assets. Use it only with files from a game you own.
