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

| Command/Variable    | Arguments | Series           | Hidden |
|---------------------|-----------|------------------|--------|
| `addt`              | 3         | `T0 T1 K0 X3 X5` |        |
| `btlen`             | 2         | `T0 T1 K0 X3 X5` |        |
| `cfgpio`            | 7         | `-- -- K0 X3 X5` |        |
| `cir`               | 3         | `T0 T1 K0 X3 X5` |        |
| `cirs`              | 4         | `T0 T1 K0 X3 X5` |        |
| `cle`               | 2         | `T0 T1 K0 X3 X5` |        |
| `click`             | 2         | `T0 T1 K0 X3 X5` |        |
| `cls`               | 1         | `T0 T1 K0 X3 X5` |        |
| `code_c`            | 0         | `T0 T1 K0 X3 X5` |        |
| `com_star`          | 0         | `T0 T1 K0 X3 X5` |        |
| `com_stop`          | 3         | `T0 T1 K0 X3 X5` |        |
| `comok`             | 4         | `T0 T1 K0 X3 X5` |        |
| `cov`               | 1         | `T0 T1 K0 X3 X5` |        |
| `covx`              | 2         | `T0 T1 K0 X3 X5` |        |
| `crcputh`           | 2         | `T0 T1 K0 X3 X5` |        |
| `crcputs`           | 2         | `T0 T1 K0 X3 X5` |        |
| `crcputu`           | 0         | `T0 T1 K0 X3 X5` |        |
| `crcrest`           | 5         | `T0 T1 K0 X3 X5` |        |
| `deldir`            | 2         | `-- -- -- X3 X5` |        |
| `delfile`           | 1         | `-- -- -- X3 X5` |        |
| `doevents`          | 2         | `T0 T1 K0 X3 X5` |        |
| `draw`              | 2         | `T0 T1 -- X3 X5` |        |
| `draw_h`            | 13        | `T0 T1 K0 X3 X5` | Y      |
| `draw3d`            | 7         | `T0 T1 K0 X3 X5` | Y      |
| `fill`              | 1         | `T0 T1 K0 X3 X5` |        |
| `finddir`           | 5         | `-- -- -- X3 X5` |        |
| `findfile`          | 2         | `-- -- -- X3 X5` |        |
| `fstr`              | 3         | `T0 T1 K0 -- --` | Y      |
| `get`               | 7         | `T0 T1 K0 X3 X5` |        |
| `getpassw`          | 0         | `T0 T1 K0 X3 X5` | y      |
| `i`                 | 4         | `T0 T1 K0 X3 X5` | y      |
| `init`              | 1         | `T0 T1 K0 X3 X5` | y      |
| `lcd_dev`           | 1         | `T0 T1 K0 X3 X5` | y      |
| `lcd_refx`          | 0         | `T0 T1 K0 X3 X5` | y      |
| `lhmi_cle`          | 0         | `T0 T1 K0 X3 X5` | y      |
| `line`              | 1         | `T0 T1 K0 X3 X5` |        |
| `move`              | 5         | `-- -- -- X3 X5` |        |
| `newdir`            | 4         | `-- -- -- X3 X5` |        |
| `newfile`           | 4         | `-- -- -- X3 X5` |        |
| `nstr`              | 3         | `T0 T1 K0 X3 X5` | Y      |
| `pa_q`              | 2         | `T0 T1 K0 X3 X5` | Y      |
| `pa_txt`            | 4         | `T0 T1 K0 X3 X5` | Y      |
| `page`              | 2         | `T0 T1 K0 X3 X5` |        |
| `pic`               | 1         | `T0 T1 K0 X3 X5` |        |
| `picq`              | 3         | `T0 T1 K0 X3 X5` |        |
| `play`              | 4         | `-- -- -- X3 X5` |        |
| `print`             | 5         | `T0 T1 K0 X3 X5` |        |
| `printh`            | 3         | `T0 T1 K0 X3 X5` |        |
| `prints`            | 1         | `T0 T1 K0 X3 X5` |        |
| `qrcode`            | 7         | `T0 T1 K0 X3 X5` | Y      |
| `randset`           | 1         | `T0 T1 K0 X3 X5` |        |
| `rdfile`            | 1         | `-- -- -- X3 X5` |        |
| `redir`             | 0         | `-- -- -- X3 X5` |        |
| `ref`               | 2         | `T0 T1 K0 X3 X5` |        |
| `ref_star`          | 2         | `T0 T1 K0 X3 X5` |        |
| `ref_stop`          | 1         | `T0 T1 K0 X3 X5` |        |
| `refile`            | 0         | `-- -- -- X3 X5` |        |
| `repo`              | 0         | `-- -- K0 X3 X5` |        |
| `rept`              | 0         | `-- -- K0 X3 X5` |        |
| `rest`              | 2         | `T0 T1 -- X3 X5` |        |
| `rfpt`              | 3         | `T0 T1 -- X3 X5` | Y      |
| `sendme`            | 2         | `T0 T1 K0 X3 X5` |        |
| `setbaudz`          | 1         | `T0 T1 K0 X3 X5` | Y      |
| `setbrush`          | 15        | `T0 T1 K0 X3 X5` | Y      |
| `setlayer`          | 2         | `-- -- -- X3 X5` | Y      |
| `showqq`            | 0         | `T0 T1 K0 X3 X5` | Y      |
| `spstr`             | 0         | `T0 T1 K0 X3 X5` |        |
| `strlen`            | 2         | `T0 T1 K0 X3 X5` |        |
| `strsize`           | 3         | `T0 T1 K0 X3 X5` | Y      |
| `substr`            | 4         | `T0 T1 K0 X3 X5` |        |
| `timerset`          | 4         | `T0 T1 K0 X3 X5` | Y      |
| `touch_j`           | 0         | `T0 T1 K0 X3 X5` |        |
| `tsw`               | 2         | `T0 T1 K0 X3 X5` |        |
| `twfile`            | 2         | `-- -- -- X3 X5` |        |
| `ucopy`             | 1         | `T0 T1 K0 X3 X5` |        |
| `udelete`           | 2         | `T0 T1 K0 X3 X5` |        |
| `vis`               | 2         | `T0 T1 K0 X3 X5` |        |
| `wepo`              | 2         | `-- -- K0 X3 X5` |        |
| `wept`              | 4         | `-- -- K0 X3 X5` |        |
| `wfpt`              | 3         | `T0 T1 -- X3 X5` | y      |
| `whmi_cle`          | 2         | `T0 T1 K0 X3 X5` | y      |
| `xpic`              | 7         | `T0 T1 K0 X3 X5` |        |
| `xstr`              | 11        | `T0 T1 K0 X3 X5` |        |
| `zstr`              | 5         | `T0 T1 K0 X3 X5` | Y      |

## Unlisted Instruction Details


| Instruction | Var 1 | Var 2 | Var 3      | Var 4       | Var 5   | Var 6   | Var 7 |
| ----------- | ----- | ----- | ---------- | ----------- | ------- | ------- | ----- |
| `draw3d`    | x pos | y pos | Vert Width | Horz Height | Color 1 | Color 2 | Size  |


