# FATCPY and FATDIR

FATCPY is a CP/M utility that reads files from a FAT32-formatted volume and copies them into the CP/M environment. It is invoked from the CP/M command line with a drive letter and a path pattern.

FATDIR lists the files and directories on a FAT32-formatted volume from CP/M.

## FATCPY Usage

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

If a destination file already exists, FATCPY asks
`File exists. Replace? Yes/No/All (Y/N/A):` after displaying its name.

- `Y` replaces the current file and asks again for the next existing file.
- `N` leaves the current file unchanged and skips to the next match.
- `A` replaces the current file and all subsequent existing files without asking
  again during this run.

Responses are single keys, accept either case, and do not require Enter. Other
keys repeat the question. Files that do not already exist are copied without a
prompt.

## FATCPY Examples

```text
FATCPY C: /DOCS/README.TXT
FATCPY C: /BIN/*
```

## FATCPY Notes

- The program reports success with `Copy complete`.
- Invalid usage prints:

```text
Usage: FATCPY B: /DIR/FILE.EXT or /DIR/*
```

## FATDIR Usage

List the FAT32 root directory:

```text
FATDIR
```

List a directory on the FAT32 volume:

```text
FATDIR /DIR
```

### Arguments

- `/DIR` is optional. If omitted, FATDIR lists the FAT32 root directory.
- FATDIR always reads the FAT32 CF volume.

## FATDIR Examples

```text
FATDIR
FATDIR /DOCS
FATDIR /BIN
```

## FATDIR Notes

- FATDIR displays FAT short 8.3 names.
- Entries are shown in four columns.
- File extensions, including the full stop, are aligned to the right of a 12-character name field.
- Directory entries are shown in brackets, such as `[DOCS]`.
- Invalid usage prints:

```text
Usage: FATDIR [/DIR]
```

## Build

The repository includes CP/M source files and build scripts:

- `MAKE.SUB` assembles FATCPY.
- `MAKEDIR.SUB` assembles FATDIR.
