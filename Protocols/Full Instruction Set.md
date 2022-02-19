# Full Instruction Set

## Intro 

This page lists _all_ the instructions available for Nextion - especially all those that aren't mentioned in the official [Nextion Instruction Set](https://nextion.tech/instruction-set/).

**Careful!** Some commands here (like the the `lcd_dev` command) might make your device malfunction. We simply don't know enough about them. Others, like `draw3d` are pretty much guaranteed to be safe. 

Please note that this documentation is far from being complete. The list of instructions is (likely) complete but their documentation is not (as you can see) and the existing infos might contain errors. Since no official documentation is provided for the hidden commands (unfortunately), trial and error is the only way to document them. Therefore any contributions - even a simple notification about an error - are highly welcome! 

## Command List

The following table is a list of all commands and variables available in editor v1.64.1 (at the time of writing, 1.64.1 is only available from TJC, latest Nextion version is 1.63.3). 

Hidden commands are listed first, followed by the "known" commands. That aside they're sorted alphabetically and it's marked in which series they're available using TJC's naming scheme. It's also marked whether they work properly within the Nextion Editor. Question marks indicate that it's currently unknown. You can report your results as issue and the file will be updated. 
| TJC | Nextion                |
|-----|----------------------- |
| T0  | T (Basic series)       |
| T1  | F (Discovery series)   |
| K0  | K (Enhanced series)    |
| X2  | -                      |
| X3  | -                      |
| X5  | P (Intelligent series) |
| NE  | - (Nextion Editor)     |

The _Arguments_ column gives you the number of arguments the command expects or the specific arguments required (in order, with the correct separator). Note: "Arguments" are strictly separated by commas, meaning commands like `printh` have exactly _one_ argument: a space separated list of values. Don't look at me like that, I don't make the rules. 

| Command    | Series/Editor          | Min Editor Version | Hidden | Arguments | Description                  |
|------------|------------------------|--------------------|--------|-----------|------------------------------|
| `cfguart`  | `_________X2_X3_X5_??` | 1.64.1             | hidden | 4         |                              |
| `cuts`     | `_________X2_X3_X5_??` | 1.64.1             | hidden | 7         |                              |
| `draw_h`   | `T0_T1_K0_X2_X3_X5_NE` |                    | hidden | 13: `x_start, y_start, head_length, head_angle, head_center_width, head_color, dot_color, dot_size, head_upper_height, head_lower_height, head_center_offset, head_top_width, head_bottom_width` | Draws a Gauge at runtime; capabilities similar to the Gauge component. On T0, T1, K0 devices only the first 6 arguments matter (others are ignored) since their gauge is only a line. |
| `draw3d`   | `T0 T1_K0_X2_X3_X5_NE` |                    | hidden | 7: `x_start, y_start, width, height, color_top_left, color_bottom_right, border_width` | Generates a two-color rectangle (as the border of the integrated 3D button graphics). |
| `fstr`     | `T0_T1_K0__________NE` |                    | hidden | 3: `input_int, digits_before_point, digits_after_point` | Converts an integer to an XFloat like string (see official XFloat component documentation for details). Writes the result to the topmost component (use f.ex. `ref x` plus `doevents` to bring the desired component to the top). |
| `getpassw` | `T0_T1_K0_X2_X3_X5_??` |                    | hidden | 0         |                              |
| `getv`     | `___T1_____________??` |                    | hidden | 1         |                              |
| `gets`     | `_________X2_X3_X5_??` | 1.64.1             | hidden | 2         |                              |
| `i`        | `T0_T1_K0_X2_X3_X5_NE` |                    | hidden | 4 `op_a,op_b,comp,offset` | "Inline" version of the `if` instruction. Note: just like the `if`, `while` and `for` instructions (which are based on this command), it does not work when sent over serial. Explained in the TFT file format documentation (and since `i` is such a beautiful name, it's called "cjmp, conditional jump" there): [TFT File Format](/File%20Formats/TFT.md#conditional-jump-operator-cjmp) |
| `init`     | `T0_T1_K0____X3_X5_??` |                    | hidden | 1         |                              |
| `lcd_dev`  | `T0_T1_K0_X2_X3_X5___` |                    | hidden | 1: `unknown_1 unknown_2 touch_offset_x touch_offset_y` (space separated list of 4 hex values) | Sonoff uses this command in its NSPanel firmware. The 4 values must be formatted as 4 character hex values without `0x` prefix. The specific command used by NSPanel, `lcd_dev fffb 0002 0000 0020` (-5 2 0 32), creates a (0, 32) pixel touch offset. It's not known what the other arguments do. |
| `lcd_refx` | `T0_T1_K0_X2_X3_X5_??` |                    | hidden | 0         |                              |
| `lhmi_cle` | `T0_T1_K0_X2_X3_X5_??` |                    | hidden | 0         |                              |
| `meup`     | `_________X2_X3_X5_??` | 1.64.1             | hidden | 2         |                              |
| `nstr`     | `T0_T1_K0_X2_X3_X5_NE` |                    | hidden | 3: `input_int, length, format` | Converts an integer to a number like string. Writes the result to the topmost component just like `fstr` (use f.ex. `ref x` plus `doevents` to bring the desired component to the top). `length` and `format` work exactly like the corresponding attributes of the number component. |
| `pa_q`     | `T0_T1_K0_X2_X3_X5_??` |                    | hidden | 2         |                              |
| `pa_txt`   | `T0_T1_K0_X2_X3_X5_??` |                    | hidden | 4         |                              |
| `piccolor` | `___T1_____________??` |                    | hidden | 4         |                              |
| `qrcode`   | `T0 T1_K0_X2_X3_X5_NE` |                    | hidden | 7: `x_start, y_start, size, back_color, front_color, overlay_pic_id, text`  | Draws a QR code at runtime; similar capabilities as the QR code component. |
| `rfpt`     | `T0_T1____X2_X3_X5_??` |                    | hidden | 3         |                              |
| `setbaudz` | `T0_T1_K0_X2_X3_X5_??` |                    | hidden | 1         |                              |
| `setbrush` | `T0_T1_K0_X2_X3_X5_??` |                    | hidden | 15        |                              |
| `sets`     | `_________X2_X3_X5_??` | 1.64.1             | hidden | 2         |                              |
| `showqq`   | `T0_T1_K0_X2_X3_X5_??` |                    | hidden | 0         |                              |
| `strsize`  | `T0_T1_K0_X2_X3_X5_??` |                    | hidden | 3         |                              |
| `timerset` | `T0_T1_K0_X2_X3_X5_??` |                    | hidden | 4         |                              |
| `wfpt`     | `T0_T1____X2_X3_X5_??` |                    | hidden | 3         |                              |
| `whmi_cle` | `T0_T1_K0_X2_X3_X5_??` |                    | hidden | 2         |                              |
| `xnum`     | `_________X2_X3_X5_??` | 1.64.1             | hidden | 10        |                              |
| `zstr`     | `T0_T1_K0_X2_X3_X5_??` |                    | hidden | 5 `unknown_1, unknown_2, unknown_3, unknown_4, txt` | Sets the text of the topmost component to `txt`. `unknown_1` through `4` must be set to `32767` otherwise the components text simply vanishes. The scrolling text component uses different (unknown) values but all other components use `32767`  and set/update their text with this. |
| `addt`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 3         |                              |
| `beep`     | `_________X2_X3_X5_??` | 1.64.1             |        | 1         |                              |
| `beepset`  | `_________X2_X3_X5_??` | 1.64.1             |        | 2         |                              |
| `btlen`    | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 2         |                              |
| `cfgpio`   | `______K0_X2_X3_X5_??` |                    |        | 3         |                              |
| `cir`      | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 4         |                              |
| `cirs`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 4         |                              |
| `cle`      | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 2         |                              |
| `click`    | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 2         |                              |
| `cls`      | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 1         |                              |
| `code_c`   | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 0         |                              |
| `com_star` | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 0         |                              |
| `com_stop` | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 0         |                              |
| `comok`    | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 7         |                              |
| `cov`      | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 3         |                              |
| `covx`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 4         |                              |
| `crcputh`  | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 1         |                              |
| `crcputs`  | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 2         |                              |
| `crcputu`  | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 2         |                              |
| `crcrest`  | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 2         |                              |
| `deldir`   | `_________X2_X3_X5_??` |                    |        | 1         |                              |
| `delfile`  | `_________X2_X3_X5_??` |                    |        | 1         |                              |
| `doevents` | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 0         |                              |
| `draw`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 5         |                              |
| `fill`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 5         |                              |
| `finddir`  | `_________X2_X3_X5_??` |                    |        | 2         |                              |
| `findfile` | `_________X2_X3_X5_??` |                    |        | 2         |                              |
| `get`      | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 1         |                              |
| `line`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 5         |                              |
| `move`     | `_________X2_X3_X5_NE` |                    |        | 7         |                              |
| `newdir`   | `_________X2_X3_X5_??` |                    |        | 1         |                              |
| `newfile`  | `_________X2_X3_X5_??` |                    |        | 2         |                              |
| `page`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 1         |                              |
| `pic`      | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 3         |                              |
| `picq`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 5         |                              |
| `play`     | `_________X2_X3_X5_??` |                    |        | 3         |                              |
| `print`    | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 1         |                              |
| `printh`   | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 1         |                              |
| `prints`   | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 2         |                              |
| `randset`  | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 2         |                              |
| `rdfile`   | `_________X2_X3_X5_NE` |                    |        | 4         |                              |
| `redir`    | `_________X2_X3_X5_NE` |                    |        | 2         |                              |
| `ref`      | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 1         |                              |
| `ref_star` | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 0         |                              |
| `ref_stop` | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 0         |                              |
| `refile`   | `_________X2_X3_X5_NE` |                    |        | 2         |                              |
| `repo`     | `______K0_X2_X3_X5_??` |                    |        | 2         |                              |
| `rept`     | `______K0_X2_X3_X5_??` |                    |        | 2         |                              |
| `rest`     | `T0_T1____X2_X3_X5_NE` |                    |        | 0         |                              |
| `sendme`   | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 0         |                              |
| `setlayer` | `_________X2_X3_X5_??` |                    |        | 2         |                              |
| `spstr`    | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 4         |                              |
| `strlen`   | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 2         |                              |
| `substr`   | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 4         |                              |
| `touch_j`  | `T0_T1_K0_X2_X3_X5___` |                    |        | 0         |                              |
| `tsw`      | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 2         |                              |
| `twfile`   | `_________X2_X3_X5_??` |                    |        | 2         |                              |
| `ucopy`    | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 4         |                              |
| `udelete`  | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 1         |                              |
| `vis`      | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 2         |                              |
| `wepo`     | `______K0_X2_X3_X5_??` |                    |        | 2         |                              |
| `wept`     | `______K0_X2_X3_X5_??` |                    |        | 2         |                              |
| `xpic`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 7         |                              |
| `xstr`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        | 11        |                              |

## Variables List

Most stuff is similar to the commands list above.

| Variable   | Series                 | Min Editor Version | Hidden | Description                  |
|------------|------------------------|--------------------|--------|------------------------------|
| `aph`      | `_________X2_X3_X5_NE` |                    | hidden | Alpha channel of runtime draw commands (`xstr`, `xpic`, `qrcode`, ...).  |
| `bcpu`     | `T0_T1_K0_X2_X3_X5_NE` |                    | hidden | CPU load in %                |
| `appid`    | `T0_T1_K0_X2_X3_X5_NE` |                    | hidden |                              |
| `portbusy` | `T0_T1_K0_X2_X3_X5_??` |                    | hidden |                              |
| `runmod`   | `T0_T1_K0_X2_X3_X5_NE` |                    | hidden | Returns `01 ff ff ff` ("command successful") when assigning 0, 1 or 2 to it - independently of the `bkcmd` setting. Returns nothing when assigning other values. Unsure if this is all that it does. |
| `sya0`     | `T0_T1_K0_X2_X3_X5_NE` |                    | hidden | Internal variable that may be used by the system. Althought it behaves like a global variable this can lead to issues if using it as such ([according to Patrick](https://nextion.tech/forums/topic/convert-char-to-its-respective-ascii-code/)). However, there haven't been any such reports yet even though [people have been using it](https://unofficialnextion.com/search?q=sya). |
| `sya1`     | `T0_T1_K0_X2_X3_X5_NE` |                    | hidden | See `sya0`                   |
| `tpdir`    | `T0_T1_K0_X2_X3_X5_NE` |                    | hidden |                              |
| `tprc`     | `_________X2_X3_X5_NE` |                    | hidden |                              |
| `addr`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `audio0`   | `_________X2_X3_X5_NE` |                    |        |                              |
| `audio1`   | `_________X2_X3_X5_NE` |                    |        |                              |
| `baud`     | `T0_T1_K0_X2_X3_X5___` |                    |        |                              |
| `bauds`    | `T0_T1_K0_X2_X3_X5___` |                    |        |                              |
| `bkcmd`    | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `BLACK`    | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `BLUE`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `BROWN`    | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `crcval`   | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `delay`    | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `dim`      | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `dims`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `dp`       | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `eq0`      | `_________X2_X3_X5___` |                    |        |                              |
| `eq1`      | `_________X2_X3_X5___` |                    |        |                              |
| `eq2`      | `_________X2_X3_X5___` |                    |        |                              |
| `eq3`      | `_________X2_X3_X5___` |                    |        |                              |
| `eq4`      | `_________X2_X3_X5___` |                    |        |                              |
| `eq5`      | `_________X2_X3_X5___` |                    |        |                              |
| `eq6`      | `_________X2_X3_X5___` |                    |        |                              |
| `eq7`      | `_________X2_X3_X5___` |                    |        |                              |
| `eq8`      | `_________X2_X3_X5___` |                    |        |                              |
| `eq9`      | `_________X2_X3_X5___` |                    |        |                              |
| `eqh`      | `_________X2_X3_X5___` |                    |        |                              |
| `eql`      | `_________X2_X3_X5___` |                    |        |                              |
| `eqm`      | `_________X2_X3_X5___` |                    |        |                              |
| `GRAY`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `GREEN`    | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `lowpower` | `___T1_____________??` |                    |        |                              |
| `pio0`     | `______K0_X2____X5___` |                    |        |                              |
| `pio1`     | `______K0_X2____X5___` |                    |        |                              |
| `pio2`     | `______K0_X2____X5___` |                    |        |                              |
| `pio3`     | `______K0_X2____X5___` |                    |        |                              |
| `pio4`     | `______K0_X2____X5___` |                    |        |                              |
| `pio5`     | `______K0_X2____X5___` |                    |        |                              |
| `pio6`     | `______K0_X2____X5___` |                    |        |                              |
| `pio7`     | `______K0_X2____X5___` |                    |        |                              |
| `pwm4`     | `______K0_X2____X5___` |                    |        |                              |
| `pwm5`     | `______K0_X2____X5___` |                    |        |                              |
| `pwm6`     | `______K0_X2____X5___` |                    |        |                              |
| `pwm7`     | `______K0_X2____X5___` |                    |        |                              |
| `pwmf`     | `______K0_X2____X5___` |                    |        |                              |
| `rand`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `recmod`   | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `RED`      | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `rtc0`     | `______K0_X2____X5___` |                    |        |                              |
| `rtc1`     | `______K0_X2____X5___` |                    |        |                              |
| `rtc2`     | `______K0_X2____X5___` |                    |        |                              |
| `rtc3`     | `______K0_X2____X5___` |                    |        |                              |
| `rtc4`     | `______K0_X2____X5___` |                    |        |                              |
| `rtc5`     | `______K0_X2____X5___` |                    |        |                              |
| `rtc6`     | `______K0_X2____X5___` |                    |        |                              |
| `scache`   | `_________X2_X3_X5_NE` | 1.64.1             |        |                              |
| `sendxy`   | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `sleep`    | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `spax`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `spay`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `tch0`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `tch1`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `tch2`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `tch3`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `thc`      | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `thdra`    | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `thsp`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `thup`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `usize`    | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `ussp`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `usup`     | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `volume`   | `_________X2_X3_X5___` |                    |        |                              |
| `WHITE`    | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `wup`      | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
| `YELLOW`   | `T0_T1_K0_X2_X3_X5_NE` |                    |        |                              |
