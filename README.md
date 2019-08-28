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
$ repo init -u https://github.com/codercument/kentkart-bsp-platform.git-b rocko
$ repo sync -j4
```
At the end of the commands you have every metadata you need to start work with.

To start a simple image build:

```
$: MACHINE=<machine> DISTRO=<distro> source ./setup-environment <build directory>
$: bitbake core-image-base
```
You can use any directory to host your build.

The source code is checked out at `kentkart-yocto/sources`.
