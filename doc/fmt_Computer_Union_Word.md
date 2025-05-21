# Computer Union Word File Format

Use TIS-620 for character encoding, file format is similar to [CU-Writer](fmt_CU-Writer.md) file format.

## TIS-620 CU (TIS-620 Computer Union)

TIS-620 CU differs by adding box-drawing characters. It did not have `Yamakkan (อ๎)` in EEh position.

|    | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | A | B | C | D | E | F |
|:--:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| 8x |
| 9x |   |   |   |   |   |   |   |   |   | ┐ | ┘ | │ | ┼ | ┴ | ┬ | ├ |
| Ax |   | ก | ข | ฃ | ค | ฅ | ฆ | ง | จ | ฉ | ช | ซ | ฌ | ญ | ฎ | ฏ |
| Bx | ฐ | ฑ | ฒ | ณ | ด | ต | ถ | ท | ธ | น | บ | ป | ผ | ฝ | พ | ฟ |
| Cx | ภ | ม | ย | ร | ฤ | ล | ฦ | ว | ศ | ษ | ส | ห | ฬ | อ | ฮ | ฯ |
| Dx | ะ | ั | า | ำ | ิ |  ี |  ึ |  ื |  ุ |  ู |  ฺ | ─ |   | ┌ | └ | ฿ |
| Ex | เ | แ | โ | ใ | ไ | ๅ | ๆ |  ็ |  ่ |  ้ |  ๊ |  ๋ |  ์ |  ํ | ┤ | ๏ |
| Fx | ๐ | ๑ | ๒ | ๓ | ๔ | ๕ | ๖ | ๗ | ๘ | ๙ | ๚ | ๛ |

## Control Code

Use the same control code as [CU-Writer](fmt_CU-Writer.md).

## Table code

| TIS-620 | Character |
|:-------:|:---------:|
| 99 | ┐ |
| 9a | ┘ |
| 9b | │ |
| 9c | ┼ |
| 9d | ┴ |
| 9e | ┬ |
| 9f | ├ |
| db | ─ |
| dd | ┌ |
| de | └ |
| ee | ┤ |
