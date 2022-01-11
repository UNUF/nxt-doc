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

| Command/Variable    | Series           | Hidden |
|---------------------|------------------|--------|
| `addt`              | `T0 T1 K0 X3 X5` |        |
| `btlen`             | `T0 T1 K0 X3 X5` |        |
| `cfgpio`            | `-- -- K0 X3 X5` |        |
| `cir`               | `T0 T1 K0 X3 X5` |        |
| `cirs`              | `T0 T1 K0 X3 X5` |        |
| `cle`               | `T0 T1 K0 X3 X5` |        |
| `click`             | `T0 T1 K0 X3 X5` |        |
| `cls`               | `T0 T1 K0 X3 X5` |        |
| `code_c`            | `T0 T1 K0 X3 X5` |        |
| `com_star`          | `T0 T1 K0 X3 X5` |        |
| `com_stop`          | `T0 T1 K0 X3 X5` |        |
| `comok`             | `T0 T1 K0 X3 X5` |        |
| `cov`               | `T0 T1 K0 X3 X5` |        |
| `covx`              | `T0 T1 K0 X3 X5` |        |
| `crcputh`           | `T0 T1 K0 X3 X5` |        |
| `crcputs`           | `T0 T1 K0 X3 X5` |        |
| `crcputu`           | `T0 T1 K0 X3 X5` |        |
| `crcrest`           | `T0 T1 K0 X3 X5` |        |
| `deldir`            | `-- -- -- X3 X5` |        |
| `delfile`           | `-- -- -- X3 X5` |        |
| `doevents`          | `T0 T1 K0 X3 X5` |        |
| `draw`              | `T0 T1 -- X3 X5` |        |
| `draw_h`            | `T0 T1 K0 X3 X5` | Y      |
| `draw3d`            | `T0 T1 K0 X3 X5` | Y      |
| `fill`              | `T0 T1 K0 X3 X5` |        |
| `finddir`           | `-- -- -- X3 X5` |        |
| `findfile`          | `-- -- -- X3 X5` |        |
| `fstr`              | `T0 T1 K0 -- -- ` | Y      |
| `get`               | `T0 T1 K0 X3 X5` |        |
| `getpassw`          | `T0 T1 K0 X3 X5` | y      |
| `i`                 | `T0 T1 K0 X3 X5` | y      |
| `init`              | `T0 T1 K0 X3 X5` | y      |
| `lcd_dev`           | `T0 T1 K0 X3 X5` | y      |
| `lcd_refx`          | `T0 T1 K0 X3 X5` | y      |
| `lhmi_cle`          | `T0 T1 K0 X3 X5` | y      |
| `line`              | `T0 T1 K0 X3 X5` |        |
| `move`              | `-- -- -- X3 X5` |        |
| `newdir`            | `-- -- -- X3 X5` |        |
| `newfile`           | `-- -- -- X3 X5` |        |
| `nstr`              | `T0 T1 K0 X3 X5` | Y      |
| `pa_q`              | `T0 T1 K0 X3 X5` | Y      |
| `pa_txt`            | `T0 T1 K0 X3 X5` | Y      |
| `page`              | `T0 T1 K0 X3 X5` |        |
| `pic`               | `T0 T1 K0 X3 X5` |        |
| `picq`              | `T0 T1 K0 X3 X5` |        |
| `play`              | `-- -- -- X3 X5` |        |
| `print`             | `T0 T1 K0 X3 X5` |        |
| `printh`            | `T0 T1 K0 X3 X5` |        |
| `prints`            | `T0 T1 K0 X3 X5` |        |
| `qrcode`            | `T0 T1 K0 X3 X5` | Y      |
| `randset`           | `T0 T1 K0 X3 X5` |        |
| `rdfile`            | `-- -- -- X3 X5` |        |
| `redir`             | `-- -- -- X3 X5` |        |
| `ref`               | `T0 T1 K0 X3 X5` |        |
| `ref_star`          | `T0 T1 K0 X3 X5` |        |
| `ref_stop`          | `T0 T1 K0 X3 X5` |        |
| `refile`            | `-- -- -- X3 X5` |        |
| `repo`              | `-- -- K0 X3 X5` |        |
| `rept`              | `-- -- K0 X3 X5` |        |
| `rest`              | `T0 T1 -- X3 X5` |        |
| `rfpt`              | `T0 T1 -- X3 X5` | Y      |
| `sendme`            | `T0 T1 K0 X3 X5` |        |
| `setbaudz`          | `T0 T1 K0 X3 X5` | Y      |
| `setbrush`          | `T0 T1 K0 X3 X5` | Y      |
| `setlayer`          | `-- -- -- X3 X5` | Y      |
| `showqq`            | `T0 T1 K0 X3 X5` | Y      |
| `spstr`             | `T0 T1 K0 X3 X5` |        |
| `strlen`            | `T0 T1 K0 X3 X5` |        |
| `strsize`           | `T0 T1 K0 X3 X5` | Y      |
| `substr`            | `T0 T1 K0 X3 X5` |        |
| `timerset`          | `T0 T1 K0 X3 X5` | Y      |
| `touch_j`           | `T0 T1 K0 X3 X5` |        |
| `tsw`               | `T0 T1 K0 X3 X5` |        |
| `twfile`            | `-- -- -- X3 X5` |        |
| `ucopy`             | `T0 T1 K0 X3 X5` |        |
| `udelete`           | `T0 T1 K0 X3 X5` |        |
| `vis`               | `T0 T1 K0 X3 X5` |        |
| `wepo`              | `-- -- K0 X3 X5` |        |
| `wept`              | `-- -- K0 X3 X5` |        |
| `wfpt`              | `T0 T1 -- X3 X5` | y      |
| `whmi_cle`          | `T0 T1 K0 X3 X5` | y      |
| `xpic`              | `T0 T1 K0 X3 X5` |        |
| `xstr`              | `T0 T1 K0 X3 X5` |        |
| `zstr`              | `T0 T1 K0 X3 X5` | Y      |
