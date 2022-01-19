# Nextion TFT File Format
## Introduction
The TFT file is the "compiled" version of the Nextion source file. Its the file that is uploaded to the Nextion display. This repo is all about reverse-engineering and documenting the TFT file format.

I'm still at a very early point in the process of understanding the file format. The information here can change at any time. 

All of this is based on TFT files that have been compiled for the 5" Basic/T Model with Nextion/TJC v1.61.1.

## Overall File Structure
The file can be divided in the follwoing sections. Details about each section are given below.
* [File header](#file-header)
* [Bootloader and Ressources](#bootloader)
  * [Header](#header)
  * [Bootloader](#bootloader)
  * [Ressources](#ressources) (Pictures and Fonts)
* [User code](#user-code)
* [File CRC](#file-crc)

This structure is valid for Nextion and TJC TFT files. 

Any addresses or offsets in the following sections are relative to the beginning of that section, not relative to the file start.

## File Header

There are actually two headers following each other. Both have the same layout:

* `0x00-0x4b`: Data
* `0x4c-0xc3`: Empty (filled with `0xff`)
* `0xc4-0xc7`: Checksum over `0x00-0xc3`

The second header starts immediately after the first one, at `0xc8`. While it has the same layout, the data is actually XORed with a model dependant value. Its content is different, too. While the first header contains mostly version stuff (display model, editor version, device orientation, etc), the second header seems to contain mostly addresses and sizes, meaning what section starts where. 

The rest of the entire file header is filled with `0xff`.


### Header 1

| **Offset**      | **Meaning**                                                                                                                                                  | **Example (Default value for unknown)**                                                                            |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------|
| `0x00`          | Unknown                                                                                                                                                      | `00`                                                                                                               |
| `0x01-0x02`     | Editor major and minor version number                                                                                                                        | v**1**.**60**.2 -> `01 3C = 1 60`, v**1**.**61**.2 -> `01 3D = 1 61`                                               |
| `0x03`          | Vendor (Nextion or TJC)                                                                                                                                      | Nextion -> `0x4e = 'N'`, TJC -> `0x54 = 'T'`                                                                       |
| `0x04-0x07`     | Unknown. Possibly related to editor/bootloader version.                                                                                                      | `54 45 01 00`                                                                                                      |
| `0x08-0x09`     | Editor/bootloader version related                                                                                                                            | v1.60.2 -> `5C CE`, v1.61.1 -> `CC CF`, v1.61.2 -> `D4 CF`                                                         |
| `0x0a-0x0b`     | Unknown                                                                                                                                                      | `00 00`                                                                                                            |
| `0x0c-0x0d`     | Horizontal resolution                                                                                                                                        | `20 03 = 800`                                                                                                      |
| `0x0e-0x0f`     | Vertical resolution                                                                                                                                          | `E0 01 = 480`                                                                                                      |
| `0x10-0x13`     | Copy of display resolution                                                                                                                                   |                                                                                                                    |
| `0x14`          | Device orientation (flips a few bytes in the bootloader, too)                                                                                                | 0deg = `0x00`, 90deg = `0x01`, 180deg = `0x02`, 270deg = `0x03`                                                    |
| `0x15-0x16`     | CRC Alogrithm used for the file checksum                                                                                                                     | Byte based (Basic/Enhanced): `00 00`, Word based (Intelligent): `03 00`                                            |
| `0x17`          | Possibly editor bugfix version                                                                                                                               | v1.60.**2** -> `0x02`, v1.61.**1** -> `0x01`, v1.61.**2** -> `0x02`                                                |
| `0x18-0x19`     | Bootloader/model related (appears in [bootloader header](#header), too)                                                                                      | v1.60.2 -> `B0 13`, v1.61.1 -> `20 15`, v1.61.2 -> `28 15`                                                         |
| `0x1a-0x1b`     | Unknown                                                                                                                                                      | `02 00`                                                                                                            |
| `0x1c-0x1d`     | Unknown                                                                                                                                                      | `00 00`                                                                                                            |
| `0x1e-0x22`     | Same as `0x18-0x1b`                                                                                                                                          |                                                                                                                    |
| `0x23-0x29`     | Unknown                                                                                                                                                      | `DC 4F 00 00 32 45 01 00`                                                                                          |
| `0x2a-0x2b`     | Bootloader/model related (appears in [bootloader header](#header), too)                                                                                      | v1.60.2 -> `7E CE`, v1.61.1 -> `EE CF`, v1.61.2 -> `F6 CF`                                                         |
| `0x2c-0x2d`     | Unknown                                                                                                                                                      | `00 00`                                                                                                            |
| `0x2e-0x31`     | Checksum of the model name                                                                                                                                   | NX4827T043 -> `B1 6E 29 CA`, NX8048T050 -> `E3 3A AD 87`, NX8048T070 -> `CC BD 1F 08`, NX8048K070 -> `6A 59 F7 A1` |
| `0x32-0x33`     | Unknown                                                                                                                                                      | `21 00`                                                                                                            |
| `0x34-0x37`     | Section size of the file. Header, [Bootloader&Ressources](#bootloader-and-ressources) and [user code](#user-code) sections start at multiples of this value. | Basic/Enhanced: `00 00 01 00`, Intelligent: `00 00 02 00`                                                          |
| `0x38-0x3b`     | Unknown                                                                                                                                                      | `0C 00 00 00`                                                                                                      |
| `0x3c-0x3f`     | Total file length (number of bytes)                                                                                                                          | 206760 Bytes -> `A8 27 03 00`                                                                                      |
| `0x40-0x43`     | Unknown                                                                                                                                                      | `00 00 02 00`                                                                                                      |
| `0x44-0x47`     | Checksum (?) over bootloader and ressources section. Vendor, file size and user code changes don't affect this value.                                        |                                                                                                                    |
| `0x48-0x4b`     | Unknown                                                                                                                                                      | `00 00 00 00`                                                                                                      |
| `0x4c-0xc3`     | Unknown                                                                                                                                                      | Filled with `0xff`                                                                                                 |
| `0xc4-0xc7`     | Checksum over `0x00-0xc3`                                                                                                                                    |                                                                                                                    |                                                                                         |


### Header 2

As stated above, the data in this header is XORed with a key. Currently it is unknown how this key is generated. Additionally, the file size related values don't actually match the file size difference when changed... Definitetly more investigation needed!

| **Offset**      | **Meaning**                                          | **Example (default value for unknown)**                              |
|-----------------|------------------------------------------------------|----------------------------------------------------------------------|
| `0x00c8-0x00cb` | Size of the usercode section                         | testfile original: `D1 0D 00 00`, tesfile shorter: `3B 0E 00 00`     |
| `0x00cc-0x00cf` | Same as `0x00-0x03`                                  |                                                                      |
| `0x00d0-0x00d3` | Unknown                                              | 3                                                                    |
| `0x00d4-0x00d7` | Unknown, file size related?                          | testfile original: `5F 0E 00 00`, tesfile shorter: `F5 0D 00 00`     |
| `0x00d8-0x00db` | Start of the bootloader section                      | `00 00 01 00`                                                        |
| `0x00dc-0x00df` | Start of the user code section                       | `00 00 03 00`                                                        |
| `0x00e0-0x00e3` | Unknown, file size related?                          |                                                                      |
| `0x00e4-0x00e7` | Unknown, file size related?                          |                                                                      |
| `0x00e8-0x00eb` | Start of the picture section (end of bootloader + 1) |                                                                      |
| `0x00ec-0x00ef` | Unknown                                              | 0 on Basic/Enhanced series. Thus can be used to read the header key. |
| `0x00f0-0x00f3` | Unknown                                              | 0 same as above                                                      |
| `0x00f4-0x00f7` | Unknown                                              | 0 same as above                                                      |
| `0x00f8-0x00fb` | Start of the font section (end of pictures + 1)      |                                                                      |
| `0x00fc-0x00ff` | Unknown                                              |                                                                      |
| `0x0100-0x0103` | Unknown                                              |                                                                      |
| `0x1004-0x1007` | Number of pictures                                   |                                                                      |
| `0x1008-0x100b` | Unknown                                              |                                                                      |
| `0x100c-0x100f` | Number of fonts                                      |                                                                      |
| `0x1010-0x1013` | Unknown                                              | 3                                                                    |


## Bootloader and Ressources

The bootloader and the ressources (images, fonts) share a section. This section has its own header. 

Apparently this section is *independant* of the display resolution. NX4827T043 and NX8048T050 have the exact same header and bootloader (assuming same ressources). Another interesting point: following to the datasheet, the NX4024K032 and the NX8048K070 have different processors (48MHz vs 108MHz). However, this section contains no difference!

### Header

Assumptions so far...:
* Goes from offset `0x00` to `0x8f`
* Every value is 4 byte aligned
* Some values appear in the [file header](#file-header), too (maked in the table above).

### Bootloader

With editor v1.61.1 the bootloader goes from of `0x10080-0x2a046`. It is independant of the user code section and especially independant of the vendor. This means that TJC and Nextion use the *exact* same bootloader for the same display models. Since the content of the section is abiguous to me, I can't analyse it further. Parts of it are apparently unencrypted. Why? Because it includes the following strings:
```
Please re download the resource file
stackbot Error.....
Lcd Driver Update OK!
recursive depth exceeds the maximum value!
SYS ERROR!
Data ERROR!
this is created....
Memory Error...
freeed.....
Resource filebinver is error!
File Version is too low
The Resource file Resolution is not Fit!
Model does not match
Device Model:
File is too large for destination device
USART Update...
SIZE:
writing DATA....
SD Card INIT ERRER Pleas Check Your SD CARD is FAT32?
No Find File
The system detects multiple tft files can not be upgraded please remove the extra tft file
after  seconds beginning  update
Open File ERROR
File is too large for destination device\
SIZE:
COPY SD...
Check Data...    
Update Failed:check Error!
Lcd Driver Update Failed!
Update Successed!
Baud:
SD Card Update......
x1:
y1:
x2:
y2:
x3:
y3:
x4:
y4:
Touch Just
Touch Screen Adjust OK!
Flash Write Error...
EEprom Write Error...
LcdDriver Is Updateed
Syscom Is Updateed
```

However, other parts seem to be obfuscated like [Header 2](#header-2). Regions that contain repeating patterns, like if a bunch of small-value 32bit integers were XORed with some value. More investigations needed. 

Note: actually it is more an interpreter than a bootloader. The user code doesn't get compiled, it gets translated into byte code (see below). 

### Ressources

Pictures first, Fonts afterwars. At the beginning of a font you'll find its name as displayed in the Nextion editor. The fonts seem to be an exact copy of the corresponding .zi files. At least the beginning of a font matches the .zi file header documentation.

Haven't analyzed it further than that.

## User Code

This section contains what has been designed in the Nextion Editor. 

There are quite a few similarities between the structure of this section and the HMI file. This is not compiled machine code but rather "preprocessed" or "translated" to make it a bit easier to digest for the microcontroller. This also means that the bootloader actually is some kind of interpreter. 

Any data or code "block" is prefixed by a 4 byte value indicating the length of the following block (excluding the 4 byte length variable). 

### Operators

#### Types

There are three types of operators: unary, binary and what I call list operators. 

Unary operators are f.ex. the `++` postincrement operator. They follow the single operand (though it is imaginable that there'll be variants that prefix it).
```
[length][operand_1][operator_unary]
```
Binary operator sit inbetween of their operands. Data blocks look like this:
```
[length][operand_1][operator_binary_a][operand_2]
```
Multiple binary operators can be combined in one block - it happens when you have multiple operators in one line in your source code. Examples are given below.
```
[length][operand_1][operator_binary_a][operand_2][operator_binary_b][operand_3][operator_binary_c][operand_4]
```

List operators are followed by a specific number of operands (as defined in the Nextion instruction set), ranging from zero to >10. The operands are separated by a `0x2c` (`','`) character. Note: operators like `printh` that seem to use spaces (`0x20`, `' '`) to separate the operands are internally marked as 1-operand operators. In that way it is consistent with the others. 
```
[length][operator_list][operand_1],[operand_2],[...],[operand_last]
```

Examples are listed below under operands.

#### Encoding

The operator itself is encoded with 1 to 3 bytes. 

1 byte operators seem to be math operations only and equal the ASCII code of that operation sign. F.ex. the `=` operator is encoded with `0x3d = '='`. Combined operations like `+=` get encoded as "combined" operator: `+=` becomes `2B 3D` which are the ASCII codes of `'+'` and `'='`. It is not clear if this is an actual operator or just a short form for `a = a + b`. Unary operators are encoded in the same way.

The names of list operators are divided into two categories: up to 4 characters long and up to 8 characters long. Internally the names get padded with `'\x00'` up to a length of either 4 or 8 bytes. They're then interpreted as `uint32` or `uint64` respectively. In the TFT file list operators are encoded with 3 bytes. The first byte is always `0x09`, the third byte is `0x04` or `0x08`, depending on the length of the name. The second byte is a simple number ranging from `0` to `n-1`, `n` being the number of list operators supported by this particular model series. This also means that the encoding is specific to every model series. Because of how the bytes are arranged one can assume that the second and third byte work like a little endian `uint16`. List operators would thus be encoded as `0x09`, `0x0403` f.ex. 

There are two interesting things to note here: The `cjmp` operator (its official name is `i` but I prefer `cjmp`) is always encoded with `0x400` on all series (so far). Secondly the `jmp` operator defeats all schemes presented so far. It is encoded with `54 20`. No `0x09`, no matching ASCII characters, no idea where that comes from. 


#### List of Operators

A full list of list operators can be found here: [Full Instruction Set](/Protocols/Full%20Instruction%20Set.md#readme). The full list of series specific encodings can be found in the source of the TFTTool: https://github.com/UNUF/TFTTool/blob/main/TFTTool.py

#### Jump Operator (jmp)

`jmp` (`54 20`) is a list operator with 1 operand: `jmp offset`, where offset is the number of bytes to jump forwards (or backwards, using negative values) in code execution. It can't be used in the Nextion Editor. Example (see [Operands](#operands) for details about the general operand format):

"Intermediate" Code:
```
prints "Important!! ",0
jmp +sizeof(prints "I <3 bubbles",0)
prints "I <3 bubbles",0
prints "FREE NEXTION",0
```
Resulting hex:
```
meaning                 | hex
----------------------------------------------------------------------------------
Block length            | 13 00 00 00
prints "Important!! ",0 | 09 0F 08 22 49 6D 70 6F 72 74 61 6E 74 21 21 20 22 2C 30
Block length            | 07 00 00 00
jump +23 (0x17) bytes   | 54 20 03 17 00 00 00
Block length            | 13 00 00 00
prints "I <3 bubbles",0 | 09 0F 08 22 49 20 3C 33 20 62 75 62 62 6C 65 73 22 2C 30
Block length            | 13 00 00 00
prints "FREE NEXTION",0 | 09 0F 08 22 46 52 45 45 20 4E 45 58 54 49 4F 4E 22 2C 30
```
This code will print `Important!! FREE NEXTION`. The second print statement - which is 19 bytes long plus 4 bytes block length - is not executed because of the preceding jump operation. However, the `jmp` operator usually only occurs together with the `cjmp` operator (see below).

#### Conditional Jump Operator (cjmp)

Important: This command is actually named `i`. However, I think that causes more confusion than good so I'll call it `cjmp` here. If you want to use it in the Nextion Editor ([which you can](/Protocols/Full%20Instruction%20Set.md#readme)), you of course need to name it as the editor expects it. 

`cjmp` is a list operator with 4 operands: `cjmp op_a,op_b,comp,offset`, where: 
* op_a: lefthand operand of the condition
* op_b: righthand operand of the condition
* comp: compare operator of the condition. The following values are possible:
    * 1: `==`
    * 2: `<`
    * 3: `>`
    * 4: `<=`
    * 5: `>=`
    * 6: `!=`
* offset: If the condition evaluates to `false` (!), the executions jumps the specified number of bytes. This works like the `jmp` command described above. If the condition is `true`, no jump occurs. 

The `cjmp` operator is used together with the `jmp` operator for if/else statements, for-loops and while-loops.

This operator cannot be used in the Nextion Editor.

Example of a complete if-else flow:

Source:
```
if(sys0==0x42424242)
{
  page 1
}
else
{
  page 0
}
```
"Intermediate" code:
```
Line  Code
1     cjmp sys0,0x42424242,1,[to line 4]
2     page 1
3     jmp [to line 5]
4     page 0
```
Resulting hex:
```
----------------------------------
meaning        | hex
----------------------------------
block length   | 16 00 00 00 
cjmp           | 09 00 04 
sys0           | 05 00 00 00 00 
,0x42424242    | 2C 03 42 42 42 42 
,1             | 2C 31
,19            | 2C 03 13 00 00 00
(end of block) | 
block length   | 04 00 00 00 
page           | 09 0B 04 
1              | 31
(end of block) | 
block length   | 07 00 00 00 
jmp            | 54 20 
8              | 03 08 00 00 00
(end of block) | 
block length   | 04 00 00 00 
page           | 09 0B 04 
0              | 30
(end of block) | 

Complete hex: 16 00 00 00 09 00 04 05 00 00 00 00 2C 03 42 42 42 42 2C 31 2C 03 13 00 00 00 04 00 00 00 09 0B 04 31 07 00 00 00 54 20 03 08 00 00 00 04 00 00 00 09 0B 04 30
```

Example of a for loop:

Source:
```
for(sys0=0;sys0<5;sys0++)
{
  prints "looping",0
}
prints "done",0
```

"Intermediate" code and hex:
```
line | code                      | hex (incl. block length)
----------------------------------------------------------------------------------------------------
1    | sys0=0                    | 07 00 00 00 05 00 00 00 00 3D 30 
2    | cjmp sys0,5,2,[to line 6] | 12 00 00 00 09 00 04 05 00 00 00 00 2C 35 2C 32 2C 03 28 00 00 00 
3    | prints "looping",0        | 0E 00 00 00 09 0F 08 22 6C 6F 6F 70 69 6E 67 22 2C 30 
4    | sys0++                    | 07 00 00 00 05 00 00 00 00 2B 2B 
5    | jmp [to line 2]           | 07 00 00 00 54 20 03 C2 FF FF FF 
6    | prints "done",0           | 0B 00 00 00 09 0F 08 22 64 6F 6E 65 22 2C 30

Complete hex: 11 00 00 00 09 0F 08 22 66 6F 72 20 63 6F 6D 69 6E 67 22 2C 30 07 00 00 00 05 00 00 00 00 3D 30 12 00 00 00 09 00 04 05 00 00 00 00 2C 35 2C 32 2C 03 28 00 00 00 0E 00 00 00 09 0F 08 22 6C 6F 6F 70 69 6E 67 22 2C 30 07 00 00 00 05 00 00 00 00 2B 2B 07 00 00 00 54 20 03 C2 FF FF FF 0B 00 00 00 09 0F 08 22 64 6F 6E 65 22 2C 30
```


### Operands

Operands can be of multiple types. The type is indicated by a 1 byte prefix. No prefix seems to mean its a string (that has to be parsed).

#### List of Operand Types

```
Prefix Byte | Type                              | Abbrev.
None        | string that needs to be pased     | ss
01          | int32, Pointer to local variable  | lp
03          | int32, actual value               | vl
04          | int32, Pointer to system variable | sp
05          | int32, Pointer to global variable | gp
```
Explanations:
* Pointers to global variables are offset addresses relative to the Global Variable Data block. Taking the example given above and the C/C++ pointer notation: `&sys0 == 0x0`, `&sys1 == 0x4`, `&sys2 == 0x8`.
* Pointers to local variables seem to follow the same principle as global pointers. They are probably relative to the Local Variable Data block - which I haven't found/looked for yet.
* Pointers to system variables again seem to follow the same principles as the other pointers. Known addresses are listed under [System Variables](#system-variables).
* No type / string: Sometimes you'll find the operands as ASCII characters like you wrote them in the source code. 

Examples

```
source:  sys0=sys1*sys2
hex:     11 00 00 00  05  00 00 00 00  3D  05  04 00 00 00  2A  05  08 00 00 00
meaning: length      |gp   &sys0      | = |gp   &sys1      | * |gp   &sys2 
```

```
source:  bauds=115200
hex:     0B 00 00 00  04  08 0A 00 00  3D  03  00 C2 01 00
meaning: length      |sp  bauds       | = |vl  115200
```

```
source:  draw 21,22,23,24,25
hex:     11 00 00 00  09 1A 04  32 31  2C  32 32  2C  32 33  2C  32 34  2C  32 35
meaning: length      | draw    | "21"  |","|"22"  |","|"23"  |","|"24"  |","|"25"
```

```
source:  fill 1,4,sys0,localVar.val,b[0].bco 
hex:     1B 00 00 00  09 0D 04  31  2C  34  2C  05  00 00 00 00  2C  01  29 00 00 00   2C  62 5B 30 5D 2E 62 63 6F
meaning: length      | fill    |"1"|","|"4"|","|gp   &sys0      |","|lp  &localVar.val|","|"b[0].bco"
```

### System Variables

Like local and global variables, system variables get replaced by a 4 byte offset address, too. However, in this case the address is determined in the same way as with the list operators: one byte indicates the length of the name while the other byte is a simple number going from `0` to `n-1`, `n` being the number of system variables available on this particular model series. This once again means that the addresses are specific to the series. 

Notable differences to the list operator encodings are that the two bytes are _swapped_: the LSB encodes the name length, and only the next byte is the number of the variable. The two upper bytes are zero (like all other variables their address is always 4 bytes long). 

Once again, you can find a full list of system variables in the [Full Instruction Set](/Protocols/Full%20Instruction%20Set.md#readme) and their device specific encodings in the source of the TFTTool: https://github.com/UNUF/TFTTool/blob/main/TFTTool.py

Examples (Basic/T0 series):
```
Variable | Address
----------------------
dp       | 04 00 00 00
RED      | 04 01 00 00
WHITE    | 08 00 00 00
thdra    | 08 04 00 00
```

### Component Data Memory Layout

Components are split in two parts: a code and a data part. The code part which includes the drawing comannds sits together with the page code. The data part, which includes most of the components attributes, is either placed inside the global or the local variables data block. Its layout usually corresponds to the list of attributes in the Nextion Editor. 

Here's the list of the layout and size of component data parts:
* Text Component (type 116)
    * Total data size: 15 + txt_maxl bytes
    * 2 Bytes: font
    * 2 Bytes: bco
    * 2 Bytes: pco
    * txt_maxl Bytes: string
    * 1 Byte: xcen
    * 1 Byte: ycon
    * 1 Byte: pw
    * 1 Byte: isbr
    * 1 Byte: spax
    * 1 Byte: spay

### Structure

There are two types of structures: Blocks, indicated with `(B)`, and sections, indicated with `(S)`. Blocks have already been explained and used above. Sections have no length value prefixed. Sections can contain other sections which can contain blocks. Every section ends with `00 00 00 00`.

* (B) Global variables data
* (B) List of all pages Block
* (S) Program.s code
* (S) Page 0
* _Work in Progress_

### Global Variables Data

This block contains Program.s variables and variables of any global objects including strings. There are no names or other informations. This section is exactly as large as your global memory usage. The data in this section equals to the variable's initial values, which means that the variables do not need to be actively initialized.

For some reason there's always 1 additional global variable than the user has defined. Could be for `dp`. but it is consistent with the "Global Memory:" output of the Nextion compiler, which shows 4 additional bytes used. The additional variable is the last one of this block and initialized to 0.

#### Example

The following Program.s code
```
int sys0=0,sys1=0x40414243,sys2=34
```
Results in:
```
hex:     0C 00 00 00 00 00 00 00 43 42 41 40 22 00 00 00 00 00 00 00
meaning: length     |sys0       |sys1       |sys2       |add. var.
```

### List of all pages

This block contains a list of all pages. Each page is represented by a 4 byte "name" and its id as shown in the Nextion Editor. The order is not fixed and seems to be the order in which the pages have been edited. I guess it's identical with the order in the HMI file. 

The 4 byte "name" is generated by filling the actual page name with null characters up to a length of 14 bytes, then applying the same byte based CRC algorithm that's used elsewhere in the Nextion files.

#### Examples

Simple HMI file with two pages, `page0` and `page1`:
```
hex:     0C 00 00 00 26 79 96 AC 00 00 C3 79 01 FA 01 00
meaning: length     |page0       id=0 |page1     id=1
```

Example with more pages:
```
 page id | page name      | hex               
--------------------------|------------------
       5 | MIDI_TC_SET    | D2 CB DA 06 05 00 
       2 | Menu           | FB F0 59 15 02 00 
       1 | Identification | D8 A7 F3 1A 01 00 
       9 | Other_Settings | AB 81 4B 60 09 00 
       8 | Settings       | 5F C9 B1 70 08 00 
      10 | User_Settings  | A3 7E CA 71 0A 00 
       6 | MIDI_Chn_Set   | 3A 09 1C 8E 06 00 
       0 | Startup        | 92 E2 E6 91 00 00 
       4 | MIDI_Live      | 9E D3 1C A9 04 00 
      11 | TC_Settings    | F3 5F 57 B1 0B 00 
       3 | Simple         | C9 D7 1F B7 03 00 
      14 | Error          | F5 6E 11 D0 0E 00 
      12 | Env_Settings   | EE DC 7E D2 0C 00 
      15 | USB_NXT_Pass   | 78 C0 5B DC 0F 00 
      17 | Help_Info      | 69 E4 A9 EA 11 00 
       7 | Lightsaber     | 38 B6 EA F0 07 00 
      13 | Keyboard       | BB 78 8F F3 0D 00 
      16 | USB_ESP_Pass   | 74 ED 20 FC 10 00 

Complete data block with length: 6C 00 00 00 D2 CB DA 06 05 00 FB F0 59 15 02 00 D8 A7 F3 1A 01 00 AB 81 4B 60 09 00 5F C9 B1 70 08 00 A3 7E CA 71 0A 00 3A 09 1C 8E 06 00 92 E2 E6 91 00 00 9E D3 1C A9 04 00 F3 5F 57 B1 0B 00 C9 D7 1F B7 03 00 F5 6E 11 D0 0E 00 EE DC 7E D2 0C 00 78 C0 5B DC 0F 00 69 E4 A9 EA 11 00 38 B6 EA F0 07 00 BB 78 8F F3 0D 00 74 ED 20 FC 10 00
```

### Program.s Code

This section contains the code other than global variable initialization (see [Global Variables Data](#global-variables-data). This section always ends with a `page 0` operation block (`04 00 00 00 09 0B 04 30`). If you specify a different page in the source code, this block will still be appended (and never reached). 

#### Example

Source:
```
int sys0=0,sys1=0,sys2=0

// Set baudrate
bauds=115200

// Power on start page 1
page 1
```
Resulting section in TFT file:
```
meaning                    | hex
----------------------------------
Block length               | 0B 00 00 00 
Pointer to system variable | 04 
&(bauds)                   | 08 0A 00 00 
=                          | 3D 
int32 value                | 03 
115200                     | 00 C2 01 00 
(End of block)             | 
Block length               | 04 00 00 00 
page                       | 09 0B 04 
1 (as ASCII char)          | 31 
(End of block)             | 
Block length               | 04 00 00 00 
page                       | 09 0B 04 
0 (as ASCII char)          | 30 
(End of block)             | 
End of section             | 00 00 00 00

Complete hex: 0B 00 00 00 04 08 0A 00 00 3D 03 00 C2 01 00 04 00 00 00 09 0B 04 31 04 00 00 00 09 0B 04 30 00 00 00 00
```

### Page 0

This section contains the code for page 0. It begins with a fill command for the background. The size (fullscreen) is hardcoded to the display resolution, while the fill color is a local variable address. 

## File CRC

At the very end of the file is a CRC value. It uses the same algorithm as the HMI file. Whether it's the word- or the byte based variant of the algorithm is controlled by the [file header](#file-header)

Additionally the first (the lowest) byte of the CRC value is XORed with the bytes at the following addresses (all in the [first header](#first-header)): `0x03`, `0x2e`, `0x3c`. 
