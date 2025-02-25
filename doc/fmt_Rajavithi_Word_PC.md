# Rajavithi Word PC File Format

Early version 1.x use only KU (Kaset or เกษตร) character encoding, version 2.x can use both Kaset and TIS-620 character encoding.

The file format is similar to WordStar file format.

## Kaset-RW (Kaset Rajavithi Word PC)

This was early Thai character encoding from Department of Computer Engineering, Kasetsart University.
It was used mainly in microcomputer hardware and software before TIS-620 standard.

The character encoding did not have Thai digit, `kho khuat (ฃ)`, `kho khon (ฅ)`, `tua lue (ฦ)`, `lak khang yao (ๅ)`, `Phinthu (อฺ) ` and `Yamakkan (อ๎)`.

Kaset-RW (Kaset Rajavithi Word PC) character encoding differs by adding Thai digit (80h-89h).

**Note:** Early version 1.x did not have Thai digit, it will use Arabic number instead.

|    | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | A | B | C | D | E | F |
|:--:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| 8x | ๐ | ๑ | ๒ | ๓ | ๔ | ๕ | ๖ | ๗ | ๘ | ๙ |
| 9x |
| Ax |   | ก | ข | ค | ฆ | ง | จ | ฉ | ช | ซ | ฌ | ญ | ฎ | ฏ | ฐ | ฑ |
| Bx | ฒ | ณ | ด | ต | ถ | ท | ธ | น | บ | ป | ผ | ฝ | พ | ฟ | ภ | ม |
| Cx | ย | ร | ฤ | ล | ว | ศ | ษ | ส | ห | ฬ | อ | ฮ | ะ |   | า | ﻿ำ |
| Dx | เ | แ | โ | ใ | ไ | ๆ | ๚ | ﻿ุ | ﻿ู | ﻿ิ | ﻿ี | ﻿ึ | ﻿ื | ﻿ั | ﻿ํ | ﻿็ |
| Ex | ﻿่ | ﻿้ | ﻿๊ | ﻿๋ | ﻿์ |
| Fx |

![Rajavithi Word PC font](./resources/RW_display_font.png)

Font used by Rajavithi Word PC

## Control Code

| Hex | ASCII |       Key      |            Meaning            |
|:---:|:-----:|:--------------:|:----------------------------- |
| 01  | [SOH] | `<Ctrl><P><A>` | Toggles 12 characters/inch character size |
| 02  | [STX] | `<Ctrl><P><B>` | Toggles bold character        |
| 03  | [ETX] | `<Ctrl><P><C>` | Toggles condensed character   |
| 04  | [EOT] | `<Ctrl><P><D>` | Toggles double strike character |
| 05  | [ENQ] | `<Ctrl><P><E>` | Toggles enlarge character     |
| 0A  |  [LF] |                |                               |
| 0D  |  [CR] |                | Followed by 0A (line feed), indicate newline |
| 0E  |  [SO] | `<Ctrl><P><N>` | Toggles 10 characters/inch character size |
| 11  | [DC1] | `<Ctrl><P><Q>` | DBF record +1                 |
| 12  | [DC2] | `<Ctrl><P><R>` | DBF record -1                 |
| 13  | [DC3] | `<Ctrl><P><S>` | Toggles underline character   |
| 14  | [DC4] | `<Ctrl><P><T>` | Toggles superscript character |
| 15  | [ETB] | `<Ctrl><P><U>` | Toggles italic character      |
| 16  | [SYN] | `<Ctrl><P><V>` | Toggles subscript character   |
| 17  |  [SO] | `<Ctrl><P><W>` | Toggles 15 characters/inch character size, RW 2.0 |
| 18  | [CAN] | `<Ctrl><P><X>` | Printing in draft mode        |
| 19  |  [EM] | `<Ctrl><P><Y>` | Printing in NLQ mode          |
| 1A  | [SUB] |                | End-of-File character         |
| 1C  |  [FS] | `<Ctrl><P><0>` | Printing in font 1, RW 2.0    |
| 1D  |  [GS] | `<Ctrl><P><1>` | Printing in font 2, RW 2.0    |
| 1E  |  [RS] | `<Ctrl><P><2>` | Printing in font 3, RW 2.0    |
| 1F  |  [US] | `<Ctrl><P><3>` | Printing in font 4, RW 2.0    |
| 8D  |       |                | Soft carriage return (inserted, followed by line feed (LF) `0A` to mark soft line break at word-wrap), RW 2.3 |

## Table code

These character was use as box-drawing characters for making table in Rajavithi Word PC.

| TIS-620 | Kaset | Character |
|:-------:|:-----:|:---------:|
| 8F | 99 | ┼ |
| 90 | 9C | ┴ |
| 91 | 96 | ┬ |
| 92 | 9A | ┤ |
| 93 | 98 | ├ |
| 95 | 9E | ─ |
| 96 | 9F | │ |
| 98 | 95 | ┌ |
| 99 | 97 | ┐ |
| 9A | 9B | └ |
| 9B | 9D | ┘ |

## Dot Command

These commands are intended to be on a line by themselves, and started with the dot (.).
This meant that regular text lines couldn't start with dots.

Note: Can use lower case.

|   Command    |                       Meaning                       |
|:-------------|:----------------------------------------------------|
| .PA          | Page break                                          |
| .HEn<text>   | Print page heading (1-4)                            |
| .HRn<text>   | Print page heading at odd page (1-4)                |
| .HLn<text>   | Print page heading at even page (1-4)               |
| .MT n        | Print number of line on page heading (1-4)          |
| .FO<text>    | Print page footing                                  |
| .FR<text>    | Print page footing at odd page                      |
| .FL<text>    | Print page footing at even page                     |
| .PL n        | Set paper length in inch                            |
| .PO n        | Set left margin (0-45)                              |
| .PN n        | Set current page number (0-9999)                    |
| .TC n        | Set Thai character encoding (0=Kaset, 1=TIS-620)    |
| .!<text>     | Run DOS command                                     |
| .!!<text>    | Immediate run                                       |
| .DF<file>    | Open file contain name list in `file` for mailmerge, CSV file format |
| .RV v1,v2,v3,... | Set variable for mailmerge, Using &v1& &v2& ... on document. |
| .LS n        | Set line spacing (0-255)                            |
| .IS n        | Set Thai character level spacing (0-255)            |
| .FF n        | Feed paper up (0-255)                               |
| .RF n        | Feed paper down (0-255)                             |
| .TO n        | Set spacing from header (/300 inch) (0-9999), Laser printer only |
| .JM n        | Justify mode (1-4) 1=fixed spacing, 2=proportional spacing, 3=proportional spacing with left-right justify, 4=proportional spacing  with left justify, Laser printer only |
| .JC n;n;...  | Justify at column n, Laser printer only             |
| .PD n        | Print direction (1-4), Laser printer only           |

## Options

After end-of-file marker (1Ah), 115 byte.

### v1.x

| Offset |           Hex           | ASCII Char |            Meaning            |
|:------:|:-----------------------:|:----------:|:----------------------------- |
| 0      | 1A                      | [SUB]      | End-of-file                   |
| 1-5    | 1A 52 57 50 43          | [SUB]RWPC  | Signature                     |
| 6      | xx                      |            | Line per page                 |
| 7-16   | 00 00 00 00 01 01 01 01 00 01 |      |                               |
| 17     | xx                      |            | Left margin, column 1 start at 0 |
| 18     | 00                      |            |                               |
| 19     | xx                      |            | Right margin, column 1 start at 0 |
| 20-32  | 00 00 00 00 00 00 00 00 00 00 01 00 00 | |                           |
| 33-115 | 2D 2D 2D 2D 2D 21 2D 2D 2D 2D 21 2D ... | -----!----!-... | Tab setting |

### v2.x

| Offset |           Hex           | ASCII Char |            Meaning            |
|:------:|:-----------------------:|:----------:|:----------------------------- |
| 0      | 1A                      | [SUB]      | End-of-file                   |
| 1-5    | 1A 52 57 32 2B          | [SUB]RW2+  | Signature                     |
| 6      | xx                      |            | Line per page                 |
| 7-16   | 00 00 00 01 01 01 01 01 00 01 |      |                               |
| 17     | xx                      |            | Left margin, column 1 start at 0 |
| 18     | 00                      |            |                               |
| 19     | xx                      |            | Right margin, column 1 start at 0 |
| 20-32  | 00 00 00 00 00 00 00 00 00 00 01 00 00 | |                           |
| 33     | xx                      |            | Thai character encoding, 0=Kaset, 1=TIS-620 |
| 34-37  | 03 03 01 01             |            |                               |
| 38-70  | 00 10 04 01 00 40 10 04 01 00 40 10 04 01 00 40 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 | | Tab setting |
| 71-114 | 1A 1A 1A ...            |            |                               |
| 115    | 00                      |            |                               |
