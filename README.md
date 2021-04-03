# Nextion Documentation

## Introduction

This repository aims to document everything from the Nextion ecosystem. File formats, protocols, ...

## Content

* File Formats
	* HMI (Source file) - TBD
	* [TFT](/File%20Formats/TFT.md#readme) (Compiled binary)
	* ZI (Font) - TBD
* Protocols
	* [Upload Protocol v1.2](/Protocols/Upload%20Protocol%20v1.2.md#readme) (allows skipping)

## Other content within the UNUF group

* [TFTTool](https://github.com/UNUF/TFTTool). Python script that allows modifying TFT files (like changing from Nextion to TJC). Also allows a very rudimentary parsing of the content.
* [Nexus](https://github.com/UNUF/Nexus) - Nextion Upload Script. the reference implementation of the upload protocol v1.2.
* [Nextion TFT Uploader](https://github.com/UNUF/nextion-tft-uploader) - C# project using v1.0 of the upload protocol.
* [Nextion Font Editor](https://github.com/UNUF/nextion-font-editor). Full documentation of the Nextion .zi font files and a handy tool for modifying them.
