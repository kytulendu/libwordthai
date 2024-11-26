# iRC Standard Word File Format

Use both KU (Kaset or เกษตร) and TIS-620 for character encoding, similar to WordStar file format.

## Control Code

| Hex | ASCII |            Meaning            |
|:---:|:-----:|:----------------------------- |
| 02  | [STX] | Toggles bold mode             |
| 03  | [ETX] | Toggles color printing mode, default is black |
| 04  | [EOT] | Toggles enlarge mode          |
| 06  | [ACK] | In color printing mode, print red character |
| 07  | [BEL] | In color printing mode, print blue character |
| 08  |  [BS] | In color printing mode, print purple character |
| 0A  |  [LF] |                               |
| 0C  |  [FF] | Toggles italic mode           |
| 0D  |  [CR] | Followed by 0A (line feed), indicate newline |
| 0E  |  [SO] | In color printing mode, print yellow character |
| 10  | [DLE] | In color printing mode, print orange character |
| 11  | [DLE] | In color printing mode, print green character |
| 13  | [DC3] | Toggles underline mode        |
| 14  | [DC4] | Toggles superscript mode      |
| 16  | [SYN] | Toggles subscript mode        |
| 1A  | [SUB] | End-of-File character         |
| 8D  |       | Soft carriage return (inserted, followed by line feed (LF) `0A` to mark soft line break at word-wrap) |

## Table code

These character was use as box-drawing characters for making table in iRC Standard Word.

| Hex | Character |
|:---:|:---------:|
| 87 | ┌ |
| 88 | ┘ |
| 89 | ┼ |
| 8B | ┐ |
| 8C | └ |
| 8E | │ |
| 8F | ─ |
| 9C | ┴ |
| 9D | ┬ |
| 9E | ┤ |
| 9F | ├ |

## Dot Command

These commands are intended to be on a line by themselves, and started with the dot (.).
This meant that regular text lines couldn't start with dots.

Note: Can use lower case.

|   Command    |                       Meaning                       |
|:-------------|:----------------------------------------------------|
| .PA          | Page break                                          |

Dot command example from `README.STW`

    .lh4
    .pl40
    .mt1
    .mb1
    .op
    .bp off

## Options

After end-of-file marker (1Ah), 128 byte.

Below is example from `README.STW` from iRC Standard Word 2.1. iRC Standard Word 1.x doesn't appear to have it.

| Offset |           Hex           | ASCII Char |            Meaning            |
|:------:|:-----------------------:|:----------:|:----------------------------- |
| 0      | 1A                      | [SUB]      | End-of-file                   |
| 1      | 12                      | [DC1]      | Signature                     |
| 2-18   | 69 52 43 20 53 74 61 6e 64 61 72 64 20 57 6f 72 64 | iRC Standard Word | Signature |
| 19-20  | 2e 26                   | .&         | Unknown                       |
| 21-32  | 59 01 00 03 09 00 09 00 41 00 21 00 | | Unknown |
| 33-48  | 01 00 03 00 01 09 00 11 00 19 00 21 00 29 00 31 | | Unknown |
| 49-64  | 00 39 00 41 00 49 00 51 00 59 00 61 00 69 00 71 | | Unknown |
| 65-80  | 00 79 00 81 00 89 00 91 00 99 00 a1 00 09 00 03 | | Unknown |
| 81-96  | 45 6e 64 00 00 00 00 00 00 58 05 00 00 00 7e 0c | | Unknown |
| 97-112 | 00 00 00 b7 12 00 00 00 52 1a 00 00 00 2c 20 00 | | Unknown |
| 113-128 | 00 00 79 27 00 00 00 0f 2d 00 00 00 1c 30 00 00 | | Unknown |
