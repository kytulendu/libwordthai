# Loxley Thai Word Processor File Format

This software use Loxley Thai character encoding.

The file format is similar to WordStar file format.

## Control Code

| Hex | ASCII |       Key      |            Meaning            |
|:---:|:-----:|:--------------:|:----------------------------- |
| 01  | [SOH] | `<Ctrl><P><A>` | Toggles 12 characters/inch character size |
| 02  | [STX] | `<Ctrl><P><B>` | Toggles bold character        |
| 04  | [EOT] | `<Ctrl><P><D>` | Toggles double strike character |
| 0A  |  [LF] |                |                               |
| 0C  |  [FF] | `<Ctrl><P><L>` | Toggles italic character      |
| 0D  |  [CR] |                | Followed by 0A (line feed), indicate newline |
| 0E  |  [SO] | `<Ctrl><P><N>` | Toggles 10 characters/inch character size |
| 13  | [DC3] | `<Ctrl><P><S>` | Toggles underline character   |
| 14  | [DC4] | `<Ctrl><P><T>` | Toggles superscript character |
| 16  | [SYN] | `<Ctrl><P><V>` | Toggles subscript character   |
| 1A  | [SUB] |                | End-of-File character         |
| 8D  |       |                | Soft carriage return (inserted, followed by line feed (LF) `0A` to mark soft line break at word-wrap) |

## Dot Command

These commands are intended to be on a line by themselves, and started with the dot (.).
This meant that regular text lines couldn't start with dots.

Note: Can use lower case.

**Most of these are guessing.**

|   Command    |                       Meaning                       |
|:-------------|:----------------------------------------------------|
| .LS n        | Set line spacing (0-255)                            |
| .PL n        | Set paper length in inch                            |
| .MT n        | Print number of line on page header (1-4)           |
| .MB n        | Unknown                                             |
| .HM n        | Unknown                                             |
| .FM n        | Unknown                                             |
| .PC n        | Unknown                                             |
| .PO n        | Set left margin (0-45)                              |
| .PA          | Page break                                          |
| .CP n        | Unknown                                             |
| .HEn<text>   | Print page header (1-4)                             |
| .FO<text>    | Print page footer                                   |
| .OP n        | Unknown                                             |
| .PN n        | Set current page number (0-9999)                    |
| .CW n        | Unknown                                             |
| .DF<file>    | Open file contain name list in `file` for mailmerge, CSV file format |
| .RV v1,v2,v3,... | Set variable for mailmerge, Using &v1& &v2& ... on document. |
| .AV n        | Unknown                                             |
| .LF n        | Unknown                                             |
