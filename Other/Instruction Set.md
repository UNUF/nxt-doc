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

| Command    | Series           | Hidden | Arguments                                                                                | Description |
|------------|------------------|--------|------------------------------------------------------------------------------------------|-------------|
| `addt`     | `T0_T1_K0_X3_X5` |        | 3                                                                                        |             |
| `btlen`    | `T0_T1_K0_X3_X5` |        | 2                                                                                        |             |
| `cfgpio`   | `______K0_X3_X5` |        | 7                                                                                        |             |
| `cir`      | `T0_T1_K0_X3_X5` |        | 3                                                                                        |             |
| `cirs`     | `T0_T1_K0_X3_X5` |        | 4                                                                                        |             |
| `cle`      | `T0_T1_K0_X3_X5` |        | 2                                                                                        |             |
| `click`    | `T0_T1_K0_X3_X5` |        | 2                                                                                        |             |
| `cls`      | `T0_T1_K0_X3_X5` |        | 1                                                                                        |             |
| `code_c`   | `T0_T1_K0_X3_X5` |        | 0                                                                                        |             |
| `com_star` | `T0_T1_K0_X3_X5` |        | 0                                                                                        |             |
| `com_stop` | `T0_T1_K0_X3_X5` |        | 3                                                                                        |             |
| `comok`    | `T0_T1_K0_X3_X5` |        | 4                                                                                        |             |
| `cov`      | `T0_T1_K0_X3_X5` |        | 1                                                                                        |             |
| `covx`     | `T0_T1_K0_X3_X5` |        | 2                                                                                        |             |
| `crcputh`  | `T0_T1_K0_X3_X5` |        | 2                                                                                        |             |
| `crcputs`  | `T0_T1_K0_X3_X5` |        | 2                                                                                        |             |
| `crcputu`  | `T0_T1_K0_X3_X5` |        | 0                                                                                        |             |
| `crcrest`  | `T0_T1_K0_X3_X5` |        | 5                                                                                        |             |
| `deldir`   | `_________X3_X5` |        | 2                                                                                        |             |
| `delfile`  | `_________X3_X5` |        | 1                                                                                        |             |
| `doevents` | `T0_T1_K0_X3_X5` |        | 2                                                                                        |             |
| `draw`     | `T0_T1_K0_X3_X5` |        | 2                                                                                        |             |
| `draw_h`   | `T0_T1_K0_X3_X5` | hidden | 13                                                                                       |             |
| `draw3d`   | `T0 T1_K0_X3_X5` | hidden | 7: `x_start, y_start, width, height, color_top_left, color_bottom_right, border_width`   | Generates a two-color rectangle (as the border of the integrated 3D button graphics). |
| `fill`     | `T0_T1_K0_X3_X5` |        | 1                                                                                        |             |
| `finddir`  | `_________X3_X5` |        | 5                                                                                        |             |
| `findfile` | `_________X3_X5` |        | 2                                                                                        |             |
| `fstr`     | `T0_T1_K0______` | hidden | 3: `input_int, digits_before_point, digits_after_point`                                  | Converts an integer to a sort of float-string by copying the specified number upper most digits before the decimal point and the specified number of lower digits after the decimal point (and dropping digits inbetween). Writes result to the topmost component (use f.ex. `ref x` plus `doevents` to bring the desired component to the top). |
| `get`      | `T0_T1_K0_X3_X5` |        | 7                                                                                        |             |
| `getpassw` | `T0_T1_K0_X3_X5` | hidden | 0                                                                                        |             |
| `i`        | `T0_T1_K0_X3_X5` | hidden | 4                                                                                        |             |
| `init`     | `T0_T1_K0_X3_X5` | hidden | 1                                                                                        |             |
| `lcd_dev`  | `T0_T1_K0_X3_X5` | hidden | 1                                                                                        |             |
| `lcd_refx` | `T0_T1_K0_X3_X5` | hidden | 0                                                                                        |             |
| `lhmi_cle` | `T0_T1_K0_X3_X5` | hidden | 0                                                                                        |             |
| `line`     | `T0_T1_K0_X3_X5` |        | 1                                                                                        |             |
| `move`     | `_________X3_X5` |        | 5                                                                                        |             |
| `newdir`   | `_________X3_X5` |        | 4                                                                                        |             |
| `newfile`  | `_________X3_X5` |        | 4                                                                                        |             |
| `nstr`     | `T0_T1_K0_X3_X5` | hidden | 3                                                                                        |             |
| `pa_q`     | `T0_T1_K0_X3_X5` | hidden | 2                                                                                        |             |
| `pa_txt`   | `T0_T1_K0_X3_X5` | hidden | 4                                                                                        |             |
| `page`     | `T0_T1_K0_X3_X5` |        | 2                                                                                        |             |
| `pic`      | `T0_T1_K0_X3_X5` |        | 1                                                                                        |             |
| `picq`     | `T0_T1_K0_X3_X5` |        | 3                                                                                        |             |
| `play`     | `_________X3_X5` |        | 4                                                                                        |             |
| `print`    | `T0_T1_K0_X3_X5` |        | 5                                                                                        |             |
| `printh`   | `T0_T1_K0_X3_X5` |        | 3                                                                                        |             |
| `prints`   | `T0_T1_K0_X3_X5` |        | 1                                                                                        |             |
| `qrcode`   | `T0 T1_K0_X3_X5` | hidden | 7: `x_start, y_start, size, back_color, front_color, overlay_pic_id, text`               | Generates a QR code at runtime; similar capabilities as the QR code component. |
| `randset`  | `T0_T1_K0_X3_X5` |        | 1                                                                                        |             |
| `rdfile`   | `_________X3_X5` |        | 1                                                                                        |             |
| `redir`    | `_________X3_X5` |        | 0                                                                                        |             |
| `ref`      | `T0_T1_K0_X3_X5` |        | 2                                                                                        |             |
| `ref_star` | `T0_T1_K0_X3_X5` |        | 2                                                                                        |             |
| `ref_stop` | `T0_T1_K0_X3_X5` |        | 1                                                                                        |             |
| `refile`   | `_________X3_X5` |        | 0                                                                                        |             |
| `repo`     | `______K0_X3_X5` |        | 0                                                                                        |             |
| `rept`     | `______K0_X3_X5` |        | 0                                                                                        |             |
| `rest`     | `T0_T1____X3_X5` |        | 2                                                                                        |             |
| `rfpt`     | `T0_T1____X3_X5` | hidden | 3                                                                                        |             |
| `sendme`   | `T0_T1_K0_X3_X5` |        | 2                                                                                        |             |
| `setbaudz` | `T0_T1_K0_X3_X5` | hidden | 1                                                                                        |             |
| `setbrush` | `T0_T1_K0_X3_X5` | hidden | 15                                                                                       |             |
| `setlayer` | `_________X3_X5` | hidden | 2                                                                                        |             |
| `showqq`   | `T0_T1_K0_X3_X5` | hidden | 0                                                                                        |             |
| `spstr`    | `T0_T1_K0_X3_X5` |        | 0                                                                                        |             |
| `strlen`   | `T0_T1_K0_X3_X5` |        | 2                                                                                        |             |
| `strsize`  | `T0_T1_K0_X3_X5` | hidden | 3                                                                                        |             |
| `substr`   | `T0_T1_K0_X3_X5` |        | 4                                                                                        |             |
| `timerset` | `T0_T1_K0_X3_X5` | hidden | 4                                                                                        |             |
| `touch_j`  | `T0_T1_K0_X3_X5` |        | 0                                                                                        |             |
| `tsw`      | `T0_T1_K0_X3_X5` |        | 2                                                                                        |             |
| `twfile`   | `_________X3_X5` |        | 2                                                                                        |             |
| `ucopy`    | `T0_T1_K0_X3_X5` |        | 1                                                                                        |             |
| `udelete`  | `T0_T1_K0_X3_X5` |        | 2                                                                                        |             |
| `vis`      | `T0_T1_K0_X3_X5` |        | 2                                                                                        |             |
| `wepo`     | `______K0_X3_X5` |        | 2                                                                                        |             |
| `wept`     | `______K0_X3_X5` |        | 4                                                                                        |             |
| `wfpt`     | `T0_T1____X3_X5` | hidden | 3                                                                                        |             |
| `whmi_cle` | `T0_T1_K0_X3_X5` | hidden | 2                                                                                        |             |
| `xpic`     | `T0_T1_K0_X3_X5` |        | 7                                                                                        |             |
| `xstr`     | `T0_T1_K0_X3_X5` |        | 11                                                                                       |             |
| `zstr`     | `T0_T1_K0_X3_X5` | hidden | 5                                                                                        |             |

## Variables List

Most stuff is similar to the commands list above.

| Variable   | Series           | hidden | Description |
|------------|------------------|--------|-------------|
| `addr`     | `T0_T1_K0_X3_X5` |        |             |
| `aph`      | `_________X3_X5` | hidden |             |
| `appid`    | `T0_T1_K0_X3_X5` | hidden |             |
| `audio0`   | `_________X3_X5` |        |             |
| `audio1`   | `_________X3_X5` |        |             |
| `baud`     | `T0_T1_K0_X3_X5` |        |             |
| `bauds`    | `T0_T1_K0_X3_X5` |        |             |
| `bcpu`     | `T0_T1_K0_X3_X5` | hidden |             |
| `bkcmd`    | `T0_T1_K0_X3_X5` |        |             |
| `BLACK`    | `T0_T1_K0_X3_X5` |        |             |
| `BLUE`     | `T0_T1_K0_X3_X5` |        |             |
| `BROWN`    | `T0_T1_K0_X3_X5` |        |             |
| `crcval`   | `T0_T1_K0_X3_X5` |        |             |
| `delay`    | `T0_T1_K0_X3_X5` |        |             |
| `dim`      | `T0_T1_K0_X3_X5` |        |             |
| `dims`     | `T0_T1_K0_X3_X5` |        |             |
| `dp`       | `T0_T1_K0_X3_X5` |        |             |
| `eq0`      | `_________X3_X5` |        |             |
| `eq1`      | `_________X3_X5` |        |             |
| `eq2`      | `_________X3_X5` |        |             |
| `eq3`      | `_________X3_X5` |        |             |
| `eq4`      | `_________X3_X5` |        |             |
| `eq5`      | `_________X3_X5` |        |             |
| `eq6`      | `_________X3_X5` |        |             |
| `eq7`      | `_________X3_X5` |        |             |
| `eq8`      | `_________X3_X5` |        |             |
| `eq9`      | `_________X3_X5` |        |             |
| `eqh`      | `_________X3_X5` |        |             |
| `eql`      | `_________X3_X5` |        |             |
| `eqm`      | `_________X3_X5` |        |             |
| `GRAY`     | `T0_T1_K0_X3_X5` |        |             |
| `GREEN`    | `T0_T1_K0_X3_X5` |        |             |
| `lowpower` | `___T1_________` |        |             |
| `pio0`     | `______K0____X5` |        |             |
| `pio1`     | `______K0____X5` |        |             |
| `pio2`     | `______K0____X5` |        |             |
| `pio3`     | `______K0____X5` |        |             |
| `pio4`     | `______K0____X5` |        |             |
| `pio5`     | `______K0____X5` |        |             |
| `pio6`     | `______K0____X5` |        |             |
| `pio7`     | `______K0____X5` |        |             |
| `portbusy` | `T0_T1_K0_X3_X5` | hidden |             |
| `pwm4`     | `______K0____X5` |        |             |
| `pwm5`     | `______K0____X5` |        |             |
| `pwm6`     | `______K0____X5` |        |             |
| `pwm7`     | `______K0____X5` |        |             |
| `pwmf`     | `______K0____X5` |        |             |
| `rand`     | `T0_T1_K0_X3_X5` |        |             |
| `recmod`   | `T0_T1_K0_X3_X5` |        |             |
| `RED`      | `T0_T1_K0_X3_X5` |        |             |
| `rtc0`     | `______K0____X5` |        |             |
| `rtc1`     | `______K0____X5` |        |             |
| `rtc2`     | `______K0____X5` |        |             |
| `rtc3`     | `______K0____X5` |        |             |
| `rtc4`     | `______K0____X5` |        |             |
| `rtc5`     | `______K0____X5` |        |             |
| `rtc6`     | `______K0____X5` |        |             |
| `runmod`   | `T0_T1_K0_X3_X5` | hidden |             |
| `sendxy`   | `T0_T1_K0_X3_X5` |        |             |
| `sleep`    | `T0_T1_K0_X3_X5` |        |             |
| `spax`     | `T0_T1_K0_X3_X5` |        |             |
| `spay`     | `T0_T1_K0_X3_X5` |        |             |
| `sya0`     | `T0_T1_K0_X3_X5` | hidden |             |
| `sya1`     | `T0_T1_K0_X3_X5` | hidden |             |
| `tch0`     | `T0_T1_K0_X3_X5` |        |             |
| `tch1`     | `T0_T1_K0_X3_X5` |        |             |
| `tch2`     | `T0_T1_K0_X3_X5` |        |             |
| `tch3`     | `T0_T1_K0_X3_X5` |        |             |
| `thc`      | `T0_T1_K0_X3_X5` |        |             |
| `thdra`    | `T0_T1_K0_X3_X5` |        |             |
| `thsp`     | `T0_T1_K0_X3_X5` |        |             |
| `thup`     | `T0_T1_K0_X3_X5` |        |             |
| `tpdir`    | `T0_T1_K0_X3_X5` | hidden |             |
| `tprc`     | `_________X3_X5` | hidden |             |
| `usize`    | `T0_T1_K0_X3_X5` |        |             |
| `ussp`     | `T0_T1_K0_X3_X5` |        |             |
| `usup`     | `T0_T1_K0_X3_X5` |        |             |
| `volume`   | `_________X3_X5` |        |             |
| `WHITE`    | `T0_T1_K0_X3_X5` |        |             |
| `wup`      | `T0_T1_K0_X3_X5` |        |             |
| `YELLOW`   | `T0_T1_K0_X3_X5` |        |             |

