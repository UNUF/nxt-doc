# Upload Protocol v1.2

## Introduction

The Upload Protocol defines a serial protocol that can be used to load a TFT file on a Nextion/TJC display. Nextion only made available the documentation of v1.1 of this protocol, while their editor uses a newer version that allows skipping parts of the file. This of course speeds up the upload significantly. We call this improved version v1.2.

## How it works

v1.2 is essentially the same as v1.1. Therefore you should be comfortable with v1.1 before continuing. 

### Differences compared to v1.1

#### Upload Command
While v1.1 initiates the upload by sending 
`whmi-wri FILE_SIZE,BAUD_RATE,DONT_CARE` 

v1.2 uses 
`whmi-wris FILE_SIZE,BAUD_RATE,1` 
Note the additional `s` at the end of the command name. The meaning of the third argument is not clear. However, the editor seems to always set it to `1`. It is probably ignored like in v1.1. 

#### Acknowledge and skipping

Instead of returning a `0x05` acknowledge after every 4kB block, the device may return `0x08` followed by a 32bit integer (little endian, lowest byte first). That integer specifies the offset at which the download shall continue. The offset is relative to the file start, not to the current position. `08 00 00 11 00` means f.ex. you shall continue at offset `0x110000`. 

#### Other differences and notes

Calculating the offset seems to take more time than a simple acknowledge. I suggest to increase the timeout from 0.5s to at least 1s.

So far the devices only reply with the skip command after the very first block which contains the file header. However, the protocol itself would allow much more flexibility. Maybe the devs at TJC will make more usage of the skip feature in the future. 

The TFT file size is actually included in the TFT file at offset `0x3c-0x3f` (little endian/lowest byte first). Could be easier/faster to read than to get the file size with other methods.

For some reason the first command after the `connect` procedure never works (for me at least). Doesn't matter if I send a `FF FF FF` first or not, whatever is the next command it will fail (returns `1A FF FF FF`). My solution is to send a dummy command and then continue normally. 

## Other links

This protocol was originally documented here: https://unofficialnextion.com/t/nextion-upload-protocol-v1-2-the-fast-one/1044

An example implementation in Python can be found here: https://github.com/unuf/nexus
