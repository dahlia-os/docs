---
title: Packaging Applications for dahliaOS
permalink: developer/packaging.html
summary: Packaging guide for dahliaOS applications
---
## Packaging Applications for dahliaOS
### Introduction
Packages on dahliaOS make use of the AppImage file format for it's portability and ease of use. 
### Prerequisites
To develop packages, you will need the following prerequisites on your host system:
* build-essential
* clang
* ninja-build
* appimagetool

#### For graphical applications:
To develop graphical applications, you can use these recommended platforms or choose your own:
* Flutter SDK
* GTK 3/4
* QT

Electron applications are supported but may need to be converted to a more efficient standard in the future.

### Application Structure
Basic application packages need the following files at minimum:

* An `AppRun` file, containing the command used to launch your applications, example below:
```shell
#!/bin/bash
exec $APPDIR/demo
```
* A .desktop file with the parameters of your application, example below:
```
[Desktop Entry]
Name=Demo
Exec=demo
Terminal=true
Icon=demo
Type=Application
Categories=Utility;
```
* An icon, 
* An executable, this is your application itself

### Building an AppImage

Once you have the structure defined above, use:
```ARCH=x86_64 appimagetool MyApplication/```
to package your application for dahliaOS as an Appimage.

#### For ARM builds:
If your application needs to be built for ARM, use 
```ARCH=arm appimagetool MyApplication/```
to build a 32 bit ARMHF binary.