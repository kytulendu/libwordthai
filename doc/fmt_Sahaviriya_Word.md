# Sahaviriya Word File Format

This program have the most complex file format out of all Thai word processor.

The program use TIS-620 character encoding.

## File header

The file header is 560 bytes long.

| Offset | Size |     Hex     |               Meaning              |
|:------:|:----:|:-----------:|:---------------------------------- |
| 0      | 4    | ff 05 02 02 | Magic number                       |
| 4      | 80   | xx ...      | Document file name                 |
| 84     | 80   | xx ...      | Document content                   |
| 164    | 80   | xx ...      | Document typist                    |
| 244    | 80   | xx ...      | Document author                    |
| 324    | 80   | xx ...      | Document remark                    |
| 404    | 5    | xx ...      | Number of pages, store in decimal numbers, field are filled with 0x20 (space) |
| 409    | 10   | xx ...      | Total characters in document, 10 digits, store in decimal numbers, field are filled with 0x20 (space) |
| 419    | 3    | xx xx xx    | Paper width in column, 3 digits, store in decimal numbers, field are filled with 0x20 (space) |
| 422    | 6    | xx ...      | Number of lines? or total time editing the document? in miniutes, 6 digits, store in decimal numbers, field are filled with 0x20 (space) |
| 428    | 8    | xx ...      | Date of document creation, 8 bytes, in DD/MM/YY format |
| 436    | 8    | xx ...      | Time of document creation, 8 bytes, in HH:MM:SS format |
| 444    | 8    | xx ...      | Date of document modified, 8 bytes, in DD/MM/YY format, default is "  /  /  " |
| 452    | 8    | xx ...      | Time of document modified, 8 bytes, in HH:MM:SS format, default is "  :  :  " |
| 460    | 4    | 00 00 00 00 |  |
| 464    | 96   | xx ...      |  |
| 560    |      |             | start of text data |

## Text data


