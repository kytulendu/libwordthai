# CU-Writer File Format

Use both KU and TIS-620 for character encoding, similar to WordStar file format.

## Control Code

| Hex | ASCII Char |       Key      |            Meaning            |
|:---:|:----------:|:--------------:|:----------------------------- |
| 02  |    STX     | `<Ctrl><P><B>` | Toggles Bold mode             |
| 05  |    ENQ     | `<Ctrl><P><E>` | Toggles Enlarge mode          |
| 0A  |            |                | Soft Space                    |
| 12  |    DC2     | `<Ctrl><P><R>` | Toggles double-underline mode |
| 13  |    DC3     | `<Ctrl><P><S>` | Toggles underline mode        |
| 14  |    DC4     | `<Ctrl><P><T>` | Toggles superscript mode      |
| 16  |    SYN     | `<Ctrl><P><V>` | Toggles subscript mode        |
| 17  |    ETB     | `<Ctrl><P><W>` | Toggles italic mode           |
| 1A  |    SUB     |                | End-of-file character         |
| 1B  |            |                | Unknown, at begin of line (CW16N22) |
| 8D  |            |                | Soft Carriage Return (inserted, followed by newline CR+LF (0D 0A), to mark soft line break at word-wrap) |

### Table code

The character in hex use to create table below.

    98 95 91 95 99
    96          96
    93 95 8f 95 92
    96    96    96
    9a 95 90 95 9b

![Table](./resources/CW_table.png)

## Dot Command

These commands are intended to be on a line by themselves, and started with the dot (.).
This meant that regular text lines couldn't start with dots.

Note: Can use lower case.

    .PA                 Page break
    .PN n               Set current page number, n is integer
    .PO n               Set left margin
    .PR n               Set right margin
    .HE text            Page heading
    .FO text            Page footing
    .PT text            Page title (at front of page number, like Page 23 )
    .DF filename        Open file contain name list in filename for mailmerge, CSV file format
    .RV v1,v2,v3,...    Use value, &v1& &v2& ..., less than 15 variable,
                        variable name is less than 20 character long
                        data is less than 40 character (count space)
    .SK                 Mark end of mailmerge, at end of letter
    .CW n               Character per inch, default 10 : 5, 12, 15, 20, 10

## Options

After end of file, 110 byte, CU-Writer version 1.5 or newer.

|           Hex           | ASCII Char |            Meaning            |
|:-----------------------:|:----------:|:----------------------------- |
| 4F 50 54 20 31 2E 35 30 | OPT 1.50   | Signature                     |
| xx                      |            | 00=KU, 01=TIS-620             |
| 00 00 00 00 00 00 00 00 |            |                               |
| 00 00 00                |            |                               |
| xx xx xx xx xx xx xx    |            | Other Version : 04 21 08 42 10 84 21, CW153\CW152.DOC : 84 A1 88 C2 90 84 A1 |
| xx xx xx xx             |            | CW16 Newly saved : 08 42 10 84, CW16 Newly saved, CW153\PERIODFL.ELN : 08 40 00 00, CW152J10 Newly saved, CW16NOV\HELP, TAIRUT, CW152\CW152.DOC : 08 42 00 00, CW152J26 Newly saved, CW153 Newly saved, CW16\MATH.DOC : 00 00 00 00, CW153\CW152.DOC : 80 ... 80 (27 byte), CW153\CW15.DOC : 08 00 00 00 |
| 00 00                   |            |                               |
| 00 00 00 00 00 00 00 00 |            |                               |
| 00 00 00 00 00 00 00 00 |            |                               |
| 00 00 00 00 00          |            |                               |
| 01 00 00                |            | In CW153, newly saved file, 01 is 00, <start> |
| 00 01 00 00 00 01 00 00 |            |                               |
| 00 01 00 00 00 01 00 00 |            |                               |
| 00 01 00 00 00 01 00 00 |            |                               |
| 00 01 00 00 00 01 00 00 |            |                               |
| 00 01                   |            | <end>                         |
| 00 00 00                |            |                               |
| xx                      |            | Left margin                   |
| 00                      |            |                               |
| xx                      |            | Right margin < 256            |
| 00                      |            |                               |
| xx                      |            | Line per page                 |
| 00                      |            |                               |
| 01                      |            |                               |
| 00                      |            |                               |
| 04 00 4E 00             |            |                               |
| 13                      |            | CW16 CW152 CW153 Newly saved : 13, CW153\PERIODFL.ELN : 0D |
| 00 6E 00                |            |                               |
