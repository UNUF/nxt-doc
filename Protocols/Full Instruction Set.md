# Full Instruction Set

## Intro 

This page lists _all_ the instructions available for Nextion - especially all those that aren't mentioned in the official [Nextion Instruction Set](https://nextion.tech/instruction-set/).

**Careful!** Some commands here (like the the `lcd_dev` command) might make your device malfunction. We simply don't know enough about them. Others, like `draw3d` are pretty much guaranteed to be safe. 

## Command List

The following table is a list of all commands and variables available in editor v1.61.2. 

Hidden commands are listed first, followed by the "known" commands. That aside they're sorted alphabetically and it's marked in which series they're available using TJC's naming scheme. It's also marked whether they work properly within the Nextion Editor. Question marks indicate that it's currently unknown. You can report your results as issue and the file will be updated. 
| TJC | Nextion                |
|-----|----------------------- |
| T0  | T (Basic series)       |
| T1  | F (Discovery series)   |
| K0  | K (Enhanced series)    |
| X3  | -                      |
| X5  | P (Intelligent series) |
| NE  | - (Nextion Editor)     |

The _Arguments_ column gives you the number of arguments the command expects or the specific arguments required (in order, with the correct separator). Note: "Arguments" are strictly separated by commas, meaning commands like `printh` have exactly _one_ argument: a space separated list of values. Don't look at me like that, I don't make the rules. 

| Command    | Series/Editor       | Hidden | Arguments | Description                  |
|------------|---------------------|--------|-----------|------------------------------|
| `draw_h`   | `T0_T1_K0_X3_X5_NE` | hidden | 13: `x_start, y_start, head_length, head_angle, head_center_width, head_color, dot_color, dot_size, head_upper_height, head_lower_height, head_center_offset, head_top_width, head_bottom_width` | Draws a Gauge at runtime; capabilities similar to the Gauge component. On T0, T1, K0 devices only the first 6 arguments matter (others are ignored) since their gauge is only a line. |
| `draw3d`   | `T0 T1_K0_X3_X5_NE` | hidden | 7: `x_start, y_start, width, height, color_top_left, color_bottom_right, border_width` | Generates a two-color rectangle (as the border of the integrated 3D button graphics). |
| `fstr`     | `T0_T1_K0_______NE` | hidden | 3: `input_int, digits_before_point, digits_after_point` | Converts an integer to an XFloat like string (see official XFloat component documentation for details). Writes the result to the topmost component (use f.ex. `ref x` plus `doevents` to bring the desired component to the top). |
| `getpassw` | `T0_T1_K0_X3_X5_??` | hidden | 0         |                              |
| `i`        | `T0_T1_K0_X3_X5_??` | hidden | 4 `op_a,op_b,comp,offset` | "Inline" version of the `if` instruction. Explained in the TFT file format documentation (and since `i` is such a beautiful name, it's called "cjmp, conditional jump" there): https://github.com/UNUF/nxt-doc/blob/main/File%20Formats/TFT.md#conditional-jump-operator-cjmp |
| `init`     | `T0_T1_K0_X3_X5_??` | hidden | 1         |                              |
| `lcd_dev`  | `T0_T1_K0_X3_X5___` | hidden | 1: `unknown_1 unknown_2 touch_offset_x touch_offset_y` (space separated list of 4 hex values) | Sonoff uses this command in its NSPanel firmware. The 4 values must be formatted as 4 character hex values without `0x` prefix. The specific command used by NSPanel, `lcd_dev fffb 0002 0000 0020` (-5 2 0 32), creates a (0, 32) pixel touch offset. It's not known what the other arguments do. |
| `lcd_refx` | `T0_T1_K0_X3_X5_??` | hidden | 0         |                              |
| `lhmi_cle` | `T0_T1_K0_X3_X5_??` | hidden | 0         |                              |
| `nstr`     | `T0_T1_K0_X3_X5_??` | hidden | 3         |                              |
| `pa_q`     | `T0_T1_K0_X3_X5_??` | hidden | 2         |                              |
| `pa_txt`   | `T0_T1_K0_X3_X5_??` | hidden | 4         |                              |
| `qrcode`   | `T0 T1_K0_X3_X5_NE` | hidden | 7: `x_start, y_start, size, back_color, front_color, overlay_pic_id, text`  | Draws a QR code at runtime; similar capabilities as the QR code component. |
| `rfpt`     | `T0_T1____X3_X5_??` | hidden | 3         |                              |
| `setbaudz` | `T0_T1_K0_X3_X5_??` | hidden | 1         |                              |
| `setbrush` | `T0_T1_K0_X3_X5_??` | hidden | 15        |                              |
| `setlayer` | `_________X3_X5_??` | hidden | 2         |                              |
| `showqq`   | `T0_T1_K0_X3_X5_??` | hidden | 0         |                              |
| `strsize`  | `T0_T1_K0_X3_X5_??` | hidden | 3         |                              |
| `timerset` | `T0_T1_K0_X3_X5_??` | hidden | 4         |                              |
| `wfpt`     | `T0_T1____X3_X5_??` | hidden | 3         |                              |
| `whmi_cle` | `T0_T1_K0_X3_X5_??` | hidden | 2         |                              |
| `zstr`     | `T0_T1_K0_X3_X5_??` | hidden | 5         |                              |
| `addt`     | `T0_T1_K0_X3_X5_NE` |        | 3         |                              |
| `btlen`    | `T0_T1_K0_X3_X5_NE` |        | 2         |                              |
| `cfgpio`   | `______K0_X3_X5_??` |        | 7         |                              |
| `cir`      | `T0_T1_K0_X3_X5_NE` |        | 3         |                              |
| `cirs`     | `T0_T1_K0_X3_X5_NE` |        | 4         |                              |
| `cle`      | `T0_T1_K0_X3_X5_NE` |        | 2         |                              |
| `click`    | `T0_T1_K0_X3_X5_NE` |        | 2         |                              |
| `cls`      | `T0_T1_K0_X3_X5_NE` |        | 1         |                              |
| `code_c`   | `T0_T1_K0_X3_X5_NE` |        | 0         |                              |
| `com_star` | `T0_T1_K0_X3_X5_NE` |        | 0         |                              |
| `com_stop` | `T0_T1_K0_X3_X5_NE` |        | 3         |                              |
| `comok`    | `T0_T1_K0_X3_X5_NE` |        | 4         |                              |
| `cov`      | `T0_T1_K0_X3_X5_NE` |        | 1         |                              |
| `covx`     | `T0_T1_K0_X3_X5_NE` |        | 2         |                              |
| `crcputh`  | `T0_T1_K0_X3_X5_NE` |        | 2         |                              |
| `crcputs`  | `T0_T1_K0_X3_X5_NE` |        | 2         |                              |
| `crcputu`  | `T0_T1_K0_X3_X5_NE` |        | 0         |                              |
| `crcrest`  | `T0_T1_K0_X3_X5_NE` |        | 5         |                              |
| `deldir`   | `_________X3_X5_??` |        | 2         |                              |
| `delfile`  | `_________X3_X5_??` |        | 1         |                              |
| `doevents` | `T0_T1_K0_X3_X5_NE` |        | 2         |                              |
| `draw`     | `T0_T1_K0_X3_X5_NE` |        | 2         |                              |
| `fill`     | `T0_T1_K0_X3_X5_NE` |        | 1         |                              |
| `finddir`  | `_________X3_X5_??` |        | 5         |                              |
| `findfile` | `_________X3_X5_??` |        | 2         |                              |
| `get`      | `T0_T1_K0_X3_X5_NE` |        | 7         |                              |
| `line`     | `T0_T1_K0_X3_X5_NE` |        | 1         |                              |
| `move`     | `_________X3_X5_NE` |        | 5         |                              |
| `newdir`   | `_________X3_X5_??` |        | 4         |                              |
| `newfile`  | `_________X3_X5_??` |        | 4         |                              |
| `page`     | `T0_T1_K0_X3_X5_NE` |        | 2         |                              |
| `pic`      | `T0_T1_K0_X3_X5_NE` |        | 1         |                              |
| `picq`     | `T0_T1_K0_X3_X5_NE` |        | 3         |                              |
| `play`     | `_________X3_X5_??` |        | 4         |                              |
| `print`    | `T0_T1_K0_X3_X5_NE` |        | 5         |                              |
| `printh`   | `T0_T1_K0_X3_X5_NE` |        | 3         |                              |
| `prints`   | `T0_T1_K0_X3_X5_NE` |        | 1         |                              |
| `randset`  | `T0_T1_K0_X3_X5_NE` |        | 1         |                              |
| `rdfile`   | `_________X3_X5_NE` |        | 1         |                              |
| `redir`    | `_________X3_X5_NE` |        | 0         |                              |
| `ref`      | `T0_T1_K0_X3_X5_NE` |        | 2         |                              |
| `ref_star` | `T0_T1_K0_X3_X5_NE` |        | 2         |                              |
| `ref_stop` | `T0_T1_K0_X3_X5_NE` |        | 1         |                              |
| `refile`   | `_________X3_X5_NE` |        | 0         |                              |
| `repo`     | `______K0_X3_X5_??` |        | 0         |                              |
| `rept`     | `______K0_X3_X5_??` |        | 0         |                              |
| `rest`     | `T0_T1____X3_X5_NE` |        | 2         |                              |
| `sendme`   | `T0_T1_K0_X3_X5_NE` |        | 2         |                              |
| `spstr`    | `T0_T1_K0_X3_X5_NE` |        | 0         |                              |
| `strlen`   | `T0_T1_K0_X3_X5_NE` |        | 2         |                              |
| `substr`   | `T0_T1_K0_X3_X5_NE` |        | 4         |                              |
| `touch_j`  | `T0_T1_K0_X3_X5___` |        | 0         |                              |
| `tsw`      | `T0_T1_K0_X3_X5_NE` |        | 2         |                              |
| `twfile`   | `_________X3_X5_??` |        | 2         |                              |
| `ucopy`    | `T0_T1_K0_X3_X5_NE` |        | 1         |                              |
| `udelete`  | `T0_T1_K0_X3_X5_NE` |        | 2         |                              |
| `vis`      | `T0_T1_K0_X3_X5_NE` |        | 2         |                              |
| `wepo`     | `______K0_X3_X5_??` |        | 2         |                              |
| `wept`     | `______K0_X3_X5_??` |        | 4         |                              |
| `xpic`     | `T0_T1_K0_X3_X5_NE` |        | 7         |                              |
| `xstr`     | `T0_T1_K0_X3_X5_NE` |        | 11        |                              |

## Variables List

Most stuff is similar to the commands list above.

| Variable   | Series              | Hidden | Description                  |
|------------|---------------------|--------|------------------------------|
| `aph`      | `_________X3_X5_NE` | hidden | Alpha channel of runtime draw commands (`xstr`, `xpic`, `qrcode`, ...).  |
| `bcpu`     | `T0_T1_K0_X3_X5_NE` | hidden | CPU load in %                |
| `appid`    | `T0_T1_K0_X3_X5_NE` | hidden |                              |
| `portbusy` | `T0_T1_K0_X3_X5_??` | hidden |                              |
| `runmod`   | `T0_T1_K0_X3_X5_NE` | hidden | Returns `01 ff ff ff` ("command successful") when assigning 0, 1 or 2 to it - independently of the `bkcmd` setting. Returns nothing when assigning other values. Unsure if this is all that it does. |
| `sya0`     | `T0_T1_K0_X3_X5_NE` | hidden | Global variable that's used for internal testing (according to Patrick). Can be used as general purpose variable but it might vanish or be repurposed in any upcoming editor version. |
| `sya1`     | `T0_T1_K0_X3_X5_NE` | hidden | See `sya0`                   |
| `tpdir`    | `T0_T1_K0_X3_X5_NE` | hidden |                              |
| `tprc`     | `_________X3_X5_NE` | hidden |                              |
| `addr`     | `T0_T1_K0_X3_X5_NE` |        |                              |
| `audio0`   | `_________X3_X5_NE` |        |                              |
| `audio1`   | `_________X3_X5_NE` |        |                              |
| `baud`     | `T0_T1_K0_X3_X5___` |        |                              |
| `bauds`    | `T0_T1_K0_X3_X5___` |        |                              |
| `bkcmd`    | `T0_T1_K0_X3_X5_NE` |        |                              |
| `BLACK`    | `T0_T1_K0_X3_X5_NE` |        |                              |
| `BLUE`     | `T0_T1_K0_X3_X5_NE` |        |                              |
| `BROWN`    | `T0_T1_K0_X3_X5_NE` |        |                              |
| `crcval`   | `T0_T1_K0_X3_X5_NE` |        |                              |
| `delay`    | `T0_T1_K0_X3_X5_NE` |        |                              |
| `dim`      | `T0_T1_K0_X3_X5_NE` |        |                              |
| `dims`     | `T0_T1_K0_X3_X5_NE` |        |                              |
| `dp`       | `T0_T1_K0_X3_X5_NE` |        |                              |
| `eq0`      | `_________X3_X5___` |        |                              |
| `eq1`      | `_________X3_X5___` |        |                              |
| `eq2`      | `_________X3_X5___` |        |                              |
| `eq3`      | `_________X3_X5___` |        |                              |
| `eq4`      | `_________X3_X5___` |        |                              |
| `eq5`      | `_________X3_X5___` |        |                              |
| `eq6`      | `_________X3_X5___` |        |                              |
| `eq7`      | `_________X3_X5___` |        |                              |
| `eq8`      | `_________X3_X5___` |        |                              |
| `eq9`      | `_________X3_X5___` |        |                              |
| `eqh`      | `_________X3_X5___` |        |                              |
| `eql`      | `_________X3_X5___` |        |                              |
| `eqm`      | `_________X3_X5___` |        |                              |
| `GRAY`     | `T0_T1_K0_X3_X5_NE` |        |                              |
| `GREEN`    | `T0_T1_K0_X3_X5_NE` |        |                              |
| `lowpower` | `___T1__________??` |        |                              |
| `pio0`     | `______K0____X5___` |        |                              |
| `pio1`     | `______K0____X5___` |        |                              |
| `pio2`     | `______K0____X5___` |        |                              |
| `pio3`     | `______K0____X5___` |        |                              |
| `pio4`     | `______K0____X5___` |        |                              |
| `pio5`     | `______K0____X5___` |        |                              |
| `pio6`     | `______K0____X5___` |        |                              |
| `pio7`     | `______K0____X5___` |        |                              |
| `pwm4`     | `______K0____X5___` |        |                              |
| `pwm5`     | `______K0____X5___` |        |                              |
| `pwm6`     | `______K0____X5___` |        |                              |
| `pwm7`     | `______K0____X5___` |        |                              |
| `pwmf`     | `______K0____X5___` |        |                              |
| `rand`     | `T0_T1_K0_X3_X5_NE` |        |                              |
| `recmod`   | `T0_T1_K0_X3_X5_NE` |        |                              |
| `RED`      | `T0_T1_K0_X3_X5_NE` |        |                              |
| `rtc0`     | `______K0____X5___` |        |                              |
| `rtc1`     | `______K0____X5___` |        |                              |
| `rtc2`     | `______K0____X5___` |        |                              |
| `rtc3`     | `______K0____X5___` |        |                              |
| `rtc4`     | `______K0____X5___` |        |                              |
| `rtc5`     | `______K0____X5___` |        |                              |
| `rtc6`     | `______K0____X5___` |        |                              |
| `sendxy`   | `T0_T1_K0_X3_X5_NE` |        |                              |
| `sleep`    | `T0_T1_K0_X3_X5_NE` |        |                              |
| `spax`     | `T0_T1_K0_X3_X5_NE` |        |                              |
| `spay`     | `T0_T1_K0_X3_X5_NE` |        |                              |
| `tch0`     | `T0_T1_K0_X3_X5_NE` |        |                              |
| `tch1`     | `T0_T1_K0_X3_X5_NE` |        |                              |
| `tch2`     | `T0_T1_K0_X3_X5_NE` |        |                              |
| `tch3`     | `T0_T1_K0_X3_X5_NE` |        |                              |
| `thc`      | `T0_T1_K0_X3_X5_NE` |        |                              |
| `thdra`    | `T0_T1_K0_X3_X5_NE` |        |                              |
| `thsp`     | `T0_T1_K0_X3_X5_NE` |        |                              |
| `thup`     | `T0_T1_K0_X3_X5_NE` |        |                              |
| `usize`    | `T0_T1_K0_X3_X5_NE` |        |                              |
| `ussp`     | `T0_T1_K0_X3_X5_NE` |        |                              |
| `usup`     | `T0_T1_K0_X3_X5_NE` |        |                              |
| `volume`   | `_________X3_X5___` |        |                              |
| `WHITE`    | `T0_T1_K0_X3_X5_NE` |        |                              |
| `wup`      | `T0_T1_K0_X3_X5_NE` |        |                              |
| `YELLOW`   | `T0_T1_K0_X3_X5_NE` |        |                              |
