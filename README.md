# FATCPY

FATCPY is a CP/M utility that reads files from a FAT32-formatted volume and copies them into the CP/M environment. It is invoked from the CP/M command line with a drive letter and a path pattern.

## Usage

Run it as:

```text
FATCPY B: /DIR/FILE.EXT
```

or:

```text
FATCPY B: /DIR/*
```

### Arguments

- `B:` selects the FAT32 drive to inspect.
- `/DIR/FILE.EXT` copies a single file.
- `/DIR/*` copies all matching files from that directory.

Wildcards `*` and `?` are supported in the path pattern.

## Examples

```text
FATCPY C: /DOCS/README.TXT
FATCPY C: /BIN/*
```

## Notes

- The program reports success with `Copy complete`.
- Invalid usage prints:

```text
Usage: FATCPY B: /DIR/FILE.EXT or /DIR/*
```

## Build

The repository includes CP/M source files and a build script, `MAKE.SUB`, for assembling the program.
