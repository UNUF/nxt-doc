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

Additionally it's marked whether the official [Nextion Instruction Set](https://nextion.tech/instruction-set/) documents the command/variable or if it's _hidden_.

The _Arguments_ column gives you the number of arguments or the specific arguments required (in order, with the correct separator).

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
| `draw_h`            | 13                                                                                       | `T0_T1_K0_X3_X5` | hidden |             |
| `draw3d`            | 7: `x_start, y_start, width, height, color_top_left, color_bottom_right, border_width`   | `T0 T1_K0_X3_X5` | hidden | Generates a two-color rectangle (as the border of the integrated 3D button graphics). |
| `fill`              | 1                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `finddir`           | 5                                                                                        | `_________X3_X5` |        |             |
| `findfile`          | 2                                                                                        | `_________X3_X5` |        |             |
| `fstr`              | 3                                                                                        | `T0_T1_K0______` | hidden |             |
| `get`               | 7                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `getpassw`          | 0                                                                                        | `T0_T1_K0_X3_X5` | hidden |             |
| `i`                 | 4                                                                                        | `T0_T1_K0_X3_X5` | hidden |             |
| `init`              | 1                                                                                        | `T0_T1_K0_X3_X5` | hidden |             |
| `lcd_dev`           | 1                                                                                        | `T0_T1_K0_X3_X5` | hidden |             |
| `lcd_refx`          | 0                                                                                        | `T0_T1_K0_X3_X5` | hidden |             |
| `lhmi_cle`          | 0                                                                                        | `T0_T1_K0_X3_X5` | hidden |             |
| `line`              | 1                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `move`              | 5                                                                                        | `_________X3_X5` |        |             |
| `newdir`            | 4                                                                                        | `_________X3_X5` |        |             |
| `newfile`           | 4                                                                                        | `_________X3_X5` |        |             |
| `nstr`              | 3                                                                                        | `T0_T1_K0_X3_X5` | hidden |             |
| `pa_q`              | 2                                                                                        | `T0_T1_K0_X3_X5` | hidden |             |
| `pa_txt`            | 4                                                                                        | `T0_T1_K0_X3_X5` | hidden |             |
| `page`              | 2                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `pic`               | 1                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `picq`              | 3                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `play`              | 4                                                                                        | `_________X3_X5` |        |             |
| `print`             | 5                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `printh`            | 3                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `prints`            | 1                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `qrcode`            | 7: `x_start, y_start, size, back_color, front_color, overlay_pic_id, text`               | `T0 T1_K0_X3_X5` | hidden | Generates a QR code at runtime; similar capabilities as the QR code component. |
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
| `rfpt`              | 3                                                                                        | `T0_T1____X3_X5` | hidden |             |
| `sendme`            | 2                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `setbaudz`          | 1                                                                                        | `T0_T1_K0_X3_X5` | hidden |             |
| `setbrush`          | 15                                                                                       | `T0_T1_K0_X3_X5` | hidden |             |
| `setlayer`          | 2                                                                                        | `_________X3_X5` | hidden |             |
| `showqq`            | 0                                                                                        | `T0_T1_K0_X3_X5` | hidden |             |
| `spstr`             | 0                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `strlen`            | 2                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `strsize`           | 3                                                                                        | `T0_T1_K0_X3_X5` | hidden |             |
| `substr`            | 4                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `timerset`          | 4                                                                                        | `T0_T1_K0_X3_X5` | hidden |             |
| `touch_j`           | 0                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `tsw`               | 2                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `twfile`            | 2                                                                                        | `_________X3_X5` |        |             |
| `ucopy`             | 1                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `udelete`           | 2                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `vis`               | 2                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `wepo`              | 2                                                                                        | `______K0_X3_X5` |        |             |
| `wept`              | 4                                                                                        | `______K0_X3_X5` |        |             |
| `wfpt`              | 3                                                                                        | `T0_T1____X3_X5` | hidden |             |
| `whmi_cle`          | 2                                                                                        | `T0_T1_K0_X3_X5` | hidden |             |
| `xpic`              | 7                                                                                        | `T0_T1_K0_X3_X5` |        |             |
| `xstr`              | 11                                                                                       | `T0_T1_K0_X3_X5` |        |             |
| `zstr`              | 5                                                                                        | `T0_T1_K0_X3_X5` | hidden |             |
