# SCT Word Processor File Format

This program use TIS-620 character encoding.

Note: The file format documentation is not complete, due to currently only the document created with this software `PS248Z01.SCT` is avaliable.

## Control Code

| Hex | ASCII |            Meaning            |
|:---:|:-----:|:----------------------------- |
| 0A  |  [LF] |                               |
| 0D  |  [CR] | Followed by 0A (line feed), indicate newline |
| 13  | [DC3] | Toggles bold character?       |
| 1A  | [SUB] | End-of-File character         |
| 8A  |       | Soft line feed, following carriage return (CR) `0D` to mark soft line break at word-wrap |

## Table code

These character was use as box-drawing characters for making table in SCT Word Processor.

| Hex | Character |
|:---:|:---------:|
| 99 | │ |
| 9A | ─ |
| 9B | ┴ |
| 9C | ┬ |
| 9D | ├ |
| 9E | ┤ |
| 9F | ┼ |
| FB | ┐ |
| FC | └ |
| FD | ┘ |
| FE | ┌ |

## Dot Command

These commands are intended to be on a line by themselves, and started with the dot (.).
This meant that regular text lines couldn't start with dots.

Note: Can use lower case.

|   Command    |                       Meaning                       |
|:-------------|:----------------------------------------------------|
| .PA          | Page break                                          |
| .HE <text>   | Print page header                                   |
| .MTn         | Set top margin in lines                             |
| .MBn         | Set bottom margin in lines                          |
| .HMn         | Set header in lines                                 |
| .PLn         | Set line per page                                   |
| .POn         | Set left margin                                     |
| .OP          | Don't print page number                             |
| .LHn         | Set line spacing                                    |
| .CWn         | Character per inch, default 10 : 10, 12, 15, 17, 20 |
| ..<text>     | Comment, not print this line                        |
