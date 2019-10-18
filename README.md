# Kentkart BSP Release Notes

This branch is based on 

* Poky: yocto-2.4 (rocko-18.0.0)
* FSL Community BSP: rocko
* QT: 5.9.4

# Kentkart BSP Platform

To get the BSP you need to have `repo` installed and use it as:

Install the `repo` utility:

```
$: mkdir ~/bin
$: curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
$: chmod a+x ~/bin/repo
```
Download the BSP source:

```
$: PATH=${PATH}:~/bin
$: mkdir ~/kentkart-yocto
$ cd ~/kentkart-yocto
$ repo init -u https://github.com/codercument/kentkart-bsp-platform.git -b rocko
$ repo sync -j4
```
Create symbolic link to kentkart-setup-release.sh 

```
$: ln -s sources/meta-kentkart/kentkart-setup-release.sh kentkart-setup-release.sh

```

At the end of the commands you have every metadata you need to start work with.

To start a simple image build:

```
$: MACHINE=<machine> DISTRO=<distro> source kentkart-setup-release.sh  <build directory>
$: bitbake core-image-base
```
To start a QT 5 image build:

```
$: MACHINE=<machine> DISTRO=<distro> source kentkart-setup-release.sh <build directory>
$: bitbake fsl-image-qt5-validation-imx
```

You can use any directory to host your build.

The source code is checked out at `kentkart-yocto/sources`.

The following lines give some specific examples. Replace the machine names and the backends specified to customize the
commands. 

# X-11 image on i.MX 6Dual Kenttablet

```
$: DISTRO=fsl-imx-x11 MACHINE=imx6dlkenttablet source kentkart-setup-release.sh -b build-x11
$: bitbake fsl-image-validation-imx
```
This builds an X11 image without Qt 5. To build with Qt 5, use fsl-image-qt5-validation-imx instead.

# Frame Buffer image on i.MX 6Dual Kenttablet

```
$: DISTRO=fsl-imx-fb MACHINE=imx6dlkenttablet source kentkart-setup-release.sh -b build-fb
$: bitbake fsl-image-qt5-validation-imx
```
This builds Qt 5 on a frame buffer backend. To build without Qt 5, use image recipe fsl-image-validation-imx.

# XWayland image on i.MX 6Dual Kenttablet

```
$: DISTRO=fsl-imx-xwayland MACHINE=imx6dlkenttablet source kentkart-setup-release.sh -b build-xwayland
$: bitbake fsl-image-qt5-validation-imx
```
This builds an XWayland image with Qt 5. To build without Qt 5, use fsl-image-validation-imx instead.

# Wayland image on i.MX 6Dual Kenttablet

```
$: DISTRO=fsl-imx-wayland MACHINE=imx6dlkenttablet source kentkart-setup-release.sh -b build-wayland
$: bitbake fsl-image-qt5-validation-imx
```
This builds a Qt 5 Weston Wayland image. To build without Qt 5, build fsl-image-validation-imx.

