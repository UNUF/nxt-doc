# Nextion Instruction Set

## Intro 

This page documents the _full_ Nextion Instruction set - including all the hidden commands. 

## Command List

The following table is a list of all commands and variables available in editor v1.61.2. 

The commands are sorted alphabetically and it's marked in which series they're available using TJC's naming scheme:
|TJC | Nextion                |
|----|----------------------- |
|T0  | T (Basic series)       |
|T1  | F (Discovery series)   |
|K0  | K (Enhanced series)    |
|X3  | -                      |
|X5  | P (Intelligent series) |

Additionally it's marked whether the official [Nextion Instruction](https://nextion.tech/instruction-set/) set documents the command/variable.

The _Arguments_ column gives you the number of arguments or the specific arguments required.

| Command/Variable    | Arguments                                                                                | Series           | Hidden | Description |
|---------------------|------------------------------------------------------------------------------------------|------------------|--------|-------------|
| `addt`              | 3                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `btlen`             | 2                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `cfgpio`            | 7                                                                                        | `______K0_X3_X5` |        |             |
| `cir`               | 3                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `cirs`              | 4                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `cle`               | 2                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `click`             | 2                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `cls`               | 1                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `code_c`            | 0                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `com_star`          | 0                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `com_stop`          | 3                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `comok`             | 4                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `cov`               | 1                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `covx`              | 2                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `crcputh`           | 2                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `crcputs`           | 2                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `crcputu`           | 0                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `crcrest`           | 5                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `deldir`            | 2                                                                                        | `_________X3_X5` |        |             |
| `delfile`           | 1                                                                                        | `_________X3_X5` |        |             |
| `doevents`          | 2                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `draw`              | 2                                                                                        | `T0_T1____X3_X5` |        |             |
| `draw_h`            | 13                                                                                       | `T0_T1_K0_X3_X5` | Y      |             |
| `draw3d`            | 7: `x_start, y_start, width, height, color_top_left, color_bottom_right, border_width`   | `T0 T1_K0_X3_X5` | Y      | Generates a two-color rectangle (as the border of the integrated 3D button graphics). |
| `fill`              | 1                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `finddir`           | 5                                                                                        | `_________X3_X5` |        |             |
| `findfile`          | 2                                                                                        | `_________X3_X5` |        |             |
| `fstr`              | 3                                                                                        | `T0_T1_K0______` | Y      |             |
| `get`               | 7                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `getpassw`          | 0                                                                                        | `T0_T1_K0_X3_X5` | y      |             |
| `i`                 | 4                                                                                        | `T0_T1_K0_X3_X5` | y      |             |
| `init`              | 1                                                                                        | `T0_T1_K0_X3_X5` | y      |             |
| `lcd_dev`           | 1                                                                                        | `T0_T1_K0_X3_X5` | y      |             |
| `lcd_refx`          | 0                                                                                        | `T0_T1_K0_X3_X5` | y      |             |
| `lhmi_cle`          | 0                                                                                        | `T0_T1_K0_X3_X5` | y      |             |
| `line`              | 1                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `move`              | 5                                                                                        | `_________X3_X5` |        |             |
| `newdir`            | 4                                                                                        | `_________X3_X5` |        |             |
| `newfile`           | 4                                                                                        | `_________X3_X5` |        |             |
| `nstr`              | 3                                                                                        | `T0_T1_K0_X3_X5` | Y      |             |
| `pa_q`              | 2                                                                                        | `T0_T1_K0_X3_X5` | Y      |             |
| `pa_txt`            | 4                                                                                        | `T0_T1_K0_X3_X5` | Y      |             |
| `page`              | 2                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `pic`               | 1                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `picq`              | 3                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `play`              | 4                                                                                        | `_________X3_X5` |        |             |
| `print`             | 5                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `printh`            | 3                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `prints`            | 1                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `qrcode`            | 7: `x_start, y_start, size, back_color, front_color, overlay_pic_id, text`               | `T0 T1_K0_X3_X5` | Y      | Generates a QR code at runtime; similar capabilities as the QR code component. |
| `randset`           | 1                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `rdfile`            | 1                                                                                        | `_________X3_X5` |        |             |
| `redir`             | 0                                                                                        | `_________X3_X5` |        |             |
| `ref`               | 2                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `ref_star`          | 2                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `ref_stop`          | 1                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `refile`            | 0                                                                                        | `_________X3_X5` |        |             |
| `repo`              | 0                                                                                        | `______K0_X3_X5` |        |             |
| `rept`              | 0                                                                                        | `______K0_X3_X5` |        |             |
| `rest`              | 2                                                                                        | `T0_T1____X3_X5` |        |             |
| `rfpt`              | 3                                                                                        | `T0_T1____X3_X5` | Y      |             |
| `sendme`            | 2                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `setbaudz`          | 1                                                                                        | `T0_T1_K0_X3_X5` | Y      |             |
| `setbrush`          | 15                                                                                       | `T0_T1_K0_X3_X5` | Y      |             |
| `setlayer`          | 2                                                                                        | `_________X3_X5` | Y      |             |
| `showqq`            | 0                                                                                        | `T0_T1_K0_X3_X5` | Y      |             |
| `spstr`             | 0                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `strlen`            | 2                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `strsize`           | 3                                                                                        | `T0_T1_K0_X3_X5` | Y      |             |
| `substr`            | 4                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `timerset`          | 4                                                                                        | `T0_T1_K0_X3_X5` | Y      |             |
| `touch_j`           | 0                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `tsw`               | 2                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `twfile`            | 2                                                                                        | `_________X3_X5` |        |             |
| `ucopy`             | 1                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `udelete`           | 2                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `vis`               | 2                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `wepo`              | 2                                                                                        | `______K0_X3_X5` |        |             |
| `wept`              | 4                                                                                        | `______K0_X3_X5` |        |             |
| `wfpt`              | 3                                                                                        | `T0_T1____X3_X5` | y      |             |
| `whmi_cle`          | 2                                                                                        | `T0_T1_K0_X3_X5` | y      |             |
| `xpic`              | 7                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `xstr`              | 11                                                                                       | `T0_T1_K0_X3_X5` |        |             |
| `zstr`              | 5                                                                                        | `T0_T1_K0_X3_X5` | Y      |             |
