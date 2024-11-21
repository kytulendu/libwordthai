# CU-Writer File Format

Use both KU (Kaset or เกษตร) and TIS-620 for character encoding, similar to WordStar file format.

## Kaset Thai character encoding

This was early Thai character encoding from Department of Computer Engineering, Kasetsart University.
It was used mainly in microcomputer hardware and software before TIS-620 standard.

The character encoding did not have Thai digit, `kho khuat (ฃ)`, `kho khon (ฅ)`, `tua lue (ฦ)`, `lak khang yao (ๅ)`.

Kaset-CW (Kaset CU-Writer) character encoding differs by adding Thai digit (90h-99h) and `tua lue (ฦ)` (CDh).

|    | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | A | B | C | D | E | F |
|:--:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| 8x |
| 9x | ๐ | ๑ | ๒ | ๓ | ๔ | ๕ | ๖ | ๗ | ๘ | ๙ |
| Ax |   | ก | ข | ค | ฆ | ง | จ | ฉ | ช | ซ | ฌ | ญ | ฎ | ฏ | ฐ | ฑ |
| Bx | ฒ | ณ | ด | ต | ถ | ท | ธ | น | บ | ป | ผ | ฝ | พ | ฟ | ภ | ม |
| Cx | ย | ร | ฤ | ล | ว | ศ | ษ | ส | ห | ฬ | อ | ฮ | ะ | ฦ | า | ﻿ำ |
| Dx | เ | แ | โ | ใ | ไ | ๆ | ๚ | ﻿ุ | ﻿ู | ﻿ิ | ﻿ี | ﻿ึ | ﻿ื | ﻿ั | ﻿ํ | ﻿็ |
| Ex | ﻿่ | ﻿้ | ﻿๊ | ﻿๋ | ﻿์ |
| Fx |

## Control Code

| Hex | ASCII Char |       Key      |            Meaning            |
|:---:|:----------:|:--------------:|:----------------------------- |
| 02  |   [STX]    | `<Ctrl><P><B>` | Toggles Bold mode             |
| 05  |   [ENQ]    | `<Ctrl><P><E>` | Toggles Enlarge mode          |
| 0A  |   [LF]     |                |                               |
| 0D  |   [CR]     |                | Followed by 0A (line feed), indicate newline |
| 12  |   [DC2]    | `<Ctrl><P><R>` | Toggles double-underline mode |
| 13  |   [DC3]    | `<Ctrl><P><S>` | Toggles underline mode        |
| 14  |   [DC4]    | `<Ctrl><P><T>` | Toggles superscript mode      |
| 16  |   [SYN]    | `<Ctrl><P><V>` | Toggles subscript mode        |
| 17  |   [ETB]    | `<Ctrl><P><W>` | Toggles italic mode           |
| 1A  |   [SUB]    |                | End-of-file character         |
| 1B  |   [ESC]    | `<Ctrl><U><S>` | Toggles font 1, CU-Writer 1.6 |
| 1C  |    [FS]    | `<Ctrl><U><S>` | Toggles font 2, computer font style, CU-Writer 1.6 |
| 1D  |    [GS]    | `<Ctrl><U><S>` | Toggles font 3, CU-Writer 1.6 |
| 1E  |    [RS]    | `<Ctrl><U><S>` | Toggles font 4, similar to font 1 but have characters for German and French, CU-Writer 1.6 |
| 8D  |            |                | Soft Carriage Return (inserted, followed by newline CR+LF (0D 0A) to mark soft line break at word-wrap) |
| A0  |            |                | zero-width space, inserted from Thai word separator software like Rama SpellCheck and iRC ZeWrite. Used by Desktop Publishing software to help separate Thai words. This character is not displaying a visible space in the rendered text. |

### Table code

These character was use as box-drawing characters for making table in CU-Writer.

Kaset-CW character encoding have different table code.

| TIS-620 | Kaset | Character |
|:-------:|:-----:|:---------:|
| 8F | 8A | ┼ |
| 90 | 88 | ┴ |
| 91 | 89 | ┬ |
| 92 | 87 | ┤ |
| 93 | 86 | ├ |
| 95 | 85 | ─ |
| 96 | 84 | │ |
| 98 | 80 | ┌ |
| 99 | 81 | ┐ |
| 9A | 82 | └ |
| 9B | 83 | ┘ |

### CU Writer for Windows 77

CU Writer for Windows added support for BMP (Bitmap) and WMF (Windows Metafile) image in document by insert it from clipboard.

```
09 0d 0a     /* signature */
```

## Dot Command

These commands are intended to be on a line by themselves, and started with the dot (.).
This meant that regular text lines couldn't start with dots.

Note: Can use lower case.

|   Command    |                       Meaning                       |
|:-------------|:----------------------------------------------------|
| .PA          | Page break                                          |
| .PN n        | Set current page number                             |
| .PO n        | Set left margin                                     |
| .PR n        | Set right margin                                    |
| .HE text     | Page heading                                        |
| .FO text     | Page footing                                        |
| .PT text     | Page title (at front of page number, like Page 23 ) |
| .DF filename | Open file contain name list in `filename` for mailmerge, CSV file format |
| .RV v1,v2,v3,... | Set variable for mailmerge, variable name is less than 20 character long, 15 variables maximum, Using &v1& &v2& ... on document. Data is less than 40 characters (count space). |
| .SK          | Mark end of mailmerge, at end of letter             |
| .CW n        | Character per inch, default 10 : 5, 12, 15, 20, 10  |

### Math equations support in CU-Writer 1.6

From `CW16.DOC`

Printing a mathematical equation is done by starting a line (at column 1) with dot Command ".M".
The text following .M will be a mathematical equation.

There are several formats as follows:

    1. .M"Hello World"    will display Hello World
       .MHello World      same with above
       The text in quotation marks is to display that text
       The quotation marks may not be necessary if the text does not match the special symbols.

    2. .M<text1><connector><text2>
       Possible <connector>
           ^ Printing text in exponent form, <text2> in the top right corner of <text1>
           / Printing in fractional form, <text1> is on top <text2> is below
           ~ Connects <text1> and <text2>
       Example:
           - .M "x"^"y"
           - .M "abc"/"x"
           - .M "a "~"B"/"C"^"2"
       The order of precedence is ^ / and ~ respectively.
       However, we can control the order by using parentheses, for example:
           - .M (B/C)^2~ ~B/C^2
       If you want to type parentheses, put them in quotation marks.

    3. .M<function>(<text1>,<text2>,...)
       The possible <function> are as follows
           - [ ]          big brackets
           - int(a,b,c)   integrate function a from b to c, example: int(TestFunc,From,To)
           - cint(a,b,c)  close integral a from b to c, example: cint(TestFunc,From,To)
           - lim(a,b)     limit function a Condition b, example: lim("sin(x)",x->0)
           - root(x)      square root sign, example: root(4+5)
           - conj(x)      cross mark sign, example: conj(3+4i)
           - abs(x)       absolute value sign, example: abs(4/5)
           - sum(x)       sum sign, example: sum(2i+1,i=1,10)
           - pie(x)       product sign, example: pie(2x,x=1,k)
       Example:
           - .M[2/3]^6
           - .Mint("sin(x)",0,)~" dx "
           - .Mcint("sin(x)"/"cos(x)",0,2)~" "~[dx/3]
           - .Mlim("sin(x)"/x,x->0)
           - .Mroot("X"/"2+3")
           - .Mconj(x+2i)
           - .M ~sum(n(n+1),n=1,10)
           - .M ~pie("(s + a i )",i=1,n)

## Options

After end-of-file marker (1Ah), 110 byte, CU-Writer version 1.5 or newer.

| Offset |           Hex           | ASCII Char |            Meaning            |
|:------:|:-----------------------:|:----------:|:----------------------------- |
| 0      | 1A                      | [SUB]      | End-of-file                   |
| 1-8    | 4F 50 54 20 31 2E 35 30 | OPT 1.50   | Signature                     |
| 9      | xx                      |            | 00=KU, 01=TIS-620             |
| 10-20  | 00 00 00 00 00 00 00 00 00 00 00 |   |                               |
| 21-27  | xx xx xx xx xx xx xx    |            | CW153\CW152.DOC : 84 A1 88 C2 90 84 A1; Other Version : 04 21 08 42 10 84 21 |
| 28-54  | xx xx xx xx 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 | | CW16 Newly saved : 08 42 10 84 ...; CW16 Newly saved, CW153\PERIODFL.ELN : 08 40 00 00 ...; CW152J10 Newly saved, CW16NOV\HELP, TAIRUT, CW152\CW152.DOC : 08 42 00 00 ...; CW152J26 Newly saved, CW153 Newly saved, CW16\MATH.DOC : 00 00 00 00 ...; CW153\CW152.DOC : 80 ... 80 (27 byte), CW153\CW15.DOC : 08 00 00 00 ... |
| 55-94  | 01 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00 | | In CW153, newly saved file, 01 is 00 |
| 95     | xx                      |            | Left margin                   |
| 96     | 00                      |            |                               |
| 97     | xx                      |            | Right margin < 256            |
| 98     | 00                      |            |                               |
| 99     | xx                      |            | Line per page                 |
| 100    | 00                      |            |                               |
| 101    | 01                      |            |                               |
| 102    | 00                      |            |                               |
|103-106 | 04 00 4E 00             |            |                               |
| 107    | 13                      |            | CW16 CW152 CW153 Newly saved : 13; CW153\PERIODFL.ELN : 0D |
|108-110 | 00 6E 00                |            |                               |
