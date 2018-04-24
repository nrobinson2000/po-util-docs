# PO

[NAME](#NAME)  
[SYNOPSIS](#SYNOPSIS)  
[DESCRIPTION](#DESCRIPTION)  
[OPTIONS](#OPTIONS)  
[LIBRARY MANAGER](#LIBRARY MANAGER)  
[OPTIONS](#OPTIONS)  
[LIBRARY EXAMPLE MANAGER](#LIBRARY EXAMPLE MANAGER)  
[KEYBOARD SHORTCUTS](#KEYBOARD SHORTCUTS)  
[AUTHOR](#AUTHOR)  
[REPORTING BUGS](#REPORTING BUGS)  
[COPYRIGHT](#COPYRIGHT)  
[SEE ALSO](#SEE ALSO)  
[NOTES](#NOTES)  
[CREDITS](#CREDITS)  

* * *

<a name="NAME"></a>

## NAME

**po-util** − The Ultimate Local Particle Experience for Linux and macOS

<a name="SYNOPSIS"></a>

## SYNOPSIS

**po** DEVICE_TYPE COMMAND DEVICE_NAME

**po** DFU_COMMAND

**po** install [full_install_path]

**po** library LIBRARY_COMMAND

<a name="DESCRIPTION"></a>

## DESCRIPTION

Particle Offline Utility, called po-util or po, is a tool for installing and using the Particle Toolchain on Linux and macOS. Local building, firmware uploading using dfu-util or particle-cli, and library management are key features.

**po-util** supports the Photon, Electron, Core, P1, Raspberry Pi, and Redbear Duo.

<a name="OPTIONS"></a>

## OPTIONS

**install**

Download the tools needed for development. Requires sudo. You can also re-install with this command. You can optionally install to an alternate location by specifying [full_install_path].

Example: **po** install ~/particle

By default, the Particle firmware is installed in ~/github.

**build**

Locally compile code in "firmware" subdirectory using gcc-arm.

**flash**

Compile code and flash to device using dfu-util.

NOTE: You can supply another argument to "build" and "flash" to specify which firmware directory to compile.

Example:

**po** photon flash photon-firmware/

**clean**

Refresh all code (Run after switching device or directory).

**init**

Initialize your current working directory as a po-util project. You must specify which platform your project is for. You can supply another argument to specify to create a project folder. (Without this argument the current working directory is initialized as a project.) The purpose of the platform argument is to generate a ".atom-build.yml" file which provides keyboard shortcuts for using po-util within Atom. More information on the shortcuts is below.

Example:

**po** photon init somePhotonProject

**create**

Initialize a project in ~/.po-util/projects, the default project folder.

Example:

**po** create photon somePhotonProject

**open**

Open a project in the default project folder in a sub-shell for quick access. You can exit the sub-shell to return to your previous session.

Example:

**po** open somePhotonProject

**update**

Download the latest releases of Redbear Duo firmware, Particle firmware, particle-cli and po-util. You may supply another argument to choose to only update only one firmware repository, using "firmware" for Particle, and "duo" for the Redbear Duo.

**upgrade**

Recompile and update the system firmware on a device.

**ota**

Upload code Over The Air using particle-cli.

NOTE: You can sequentially flash code to multiple devices by passing the -m or --multi argument to **ota**

Example:

**po** photon ota -m product-firmware/

NOTE: This is different from the product firmware update feature in the Particle Console because it updates the firmware of devices one at a time and only if the devices are online when the command is run.

NOTE: Using -m or --multi depends on a **devices.txt** file inside of your project. The file must contain the names of your devices, one per line, and the devices must all be of the same type.

**serial open**

Put a device into listening mode.

You can specify a device with **-d**

Example:

**po** serial open -d /dev/cu.usbmodem1441

**serial monitor**

Monitor a device’s serial output using **screen** (Close with CRTL-A +D)

**config**

Select Particle firmware branch and DFU trigger baud rate.

**setup**

Get a device’s ID and connect it Wi-Fi. Manually claim it after.

**ls, list**

List devices on serial ports.

**dfu**

Flash pre-compiled code to your device.

Example:

**po photon** dfu

**dfu open**

Put a device into DFU mode.

You can specify a device with **-d**

Example:

**po** dfu open -d /dev/cu.usbmodem1441

**dfu close**

Get device out of DFU mode.

**lib, library**

Library manager command for po-util.

<a name="LIBRARY MANAGER"></a>

## LIBRARY MANAGER

**po lib**

The library manager makes it easy to use Particle libraries hosted on GitHub with your projects. It does this by keeping the library repositories in **~/.po-util/lib** and creating symbolic links to the relevant library files in your projects. It keeps track of which libraries are used in a project in a **libs.txt** file in every project. More features which are listed below.

<a name="OPTIONS"></a>

## OPTIONS

**get, install**

Download a Particle Library with Git and optionally name it. If run with no arguments, libraries listed in "libs.txt" are installed.

Example of downloading a library from GitHub:

**po lib** get https://github.com/someUser/libraryName libraryName

**add, import**

Add a downloaded library to a po-util project. Libraries are added in the firmware directory as soft links. Additionally, the library information is added to "libs.txt" so that you can keep track of your libraries and restore them in the future.

Example adding an installed library to a project:

**po lib** add libraryName

**rm, remove**

Remove a library from a po-util project. Just the soft links are deleted.

Example:

**po lib** rm libraryName

**create**

Create other libraries from other C++ files in a library. Useful for when multiple libraries are packaged together and need to be separated.

Example:

**cd** ~/.po-util/lib/someLibWithOtherLibsInside

**po lib** create

**purge**

Uninstall (delete) a library from ~/.po-util/lib

Example:

**po lib** purge someLibrary

**ls, list**

List all downloaded libraries. Libraries are kept in:

**~/.po-util/lib**

**src, source**

List all downloaded libraries that are repositories and include their Git URL’s.

**setup**

A combination of **po lib install** and **po lib add**

Libraries listed in "libs.txt" are installed and symlinks are created.

**clean**

All symlinks in the project are removed, but "libs.txt" is untouched. This is ideal for releasing you project, as there will be no linked libraries in the "firmware" directory, but rather a list that people can run "po lib setup" to download your project’s dependencies.

**pack, package, export**

Copy your source code and linked libraries in "firmware" into a packaged directory inside of your project. A tarball of the packaged directory is also created. A useful method for sharing your project with users who do not have po-util.

NOTE: If you are building for Raspberry Pi, Docker will not follow the symlinked files, and you will have to build the packaged directory instead.

**po lib pack**

**po pi build <PROJECT>-packaged**

**update, refresh**

Update your (git) libraries.

**view-headers**

View any dependencies included libraries may have.

**ex, examples**

Library example manager. Can be used to list available examples for a library and load them into a project.

<a name="LIBRARY EXAMPLE MANAGER"></a>

## LIBRARY EXAMPLE MANAGER

**po lib ex**

A work in progress. The Library Example Manger allows you to find examples in a library and load them into your project for testing or modification. Your original source code is backed up in the "main.cpp.YYYY-MM-DD-HH-mm.txt" format. A "libs.txt" will be generated from the example upon loading.

**ls, list**

List all examples in a Library.

Example:

**po lib ex** ls libraryName

**load**

Load an example from a library into the current project. A "libs.txt" will be generated from the example upon loading.

Example:

**po lib ex** load libraryName exampleName

<a name="KEYBOARD SHORTCUTS"></a>

## KEYBOARD SHORTCUTS

The following shortcuts allow you to run common po-util commands quickly while using Atom. This requires the "build" package for Atom. Get the package and a few other handy packages with: **po setup-atom**

**build**
CTRL-ALT-1

**flash**
CTRL-ALT-2

**clean**
CTRL-ALT-3

**dfu**
CTRL-ALT-4

**ota**
CTRL-ALT-5

<a name="AUTHOR"></a>

## AUTHOR

Nathan D. Robinson <nrobinson2000@me.com>

<a name="REPORTING BUGS"></a>

## REPORTING BUGS

po on GitHub: <https://github.com/nrobinson2000/po>

<a name="COPYRIGHT"></a>

## COPYRIGHT

Copyright (C) 2018 Nathan D. Robinson. License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>. This is free software: you are free to change and redistribute it. There is NO WARRANTY, to the extent permitted by law.

<a name="SEE ALSO"></a>

## SEE ALSO

Documentation available at: <https://docs.po-util.com>  
Gitter Community avaliable at: <https://gitter.im/po-util/Lobby>

<a name="NOTES"></a>

## NOTES

To build locally for Raspberry Pi you must have Docker installed.

<a name="CREDITS"></a>

## CREDITS

Some elements were inspired by GPL projects and threads on the Particle Community and StackOverflow.

* * *
