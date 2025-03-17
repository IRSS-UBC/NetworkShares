# Network Shares (ByUser and ByProject) Guide

## Table of Contents
- [Introduction](#introduction)
- [The Network Shares](#the-network-shares)
  - [ByUser and ByProject](#byuser-and-byproject)
  - [Connecting to ByUser and ByProject](#connecting-to-byuser-and-byproject)
  - [Moving Files To/From Network](#moving-files-to/from-network)
  - [Additional Notes](#additional-notes)

## Introduction
This document provides guidelines for connecting to and best practices for using the **Network Shares** (ByUser and ByProject) in the IRSS. This documentation will help ensure that this server is used to its full capacity by everyone who needs it and will help avoid conflicts with the IT department.

---

## The Network Shares

### ByUser and ByProject
ByUser and ByProject are the two network shares available for storing data. **ByUser** is a location where lab members can store data in a personal folder, making it easy to share data among lab members or with headless machines. **ByProject** is used for larger shared projects accessed by multiple members of the IRSS. You can also find useful cartographic layers for all of Canada on this share.

*Note: ByUser and ByProject are not secure places to store personal or sensitive information. Please do not store any personal data (e.g., passport numbers) or student information (e.g., student grades or names) on these shares.*

### Connecting to ByUser and ByProject
To connect to ByUser and ByProject, it is recommended to create a shortcut to the network paths. This will limit the number of active users on the shares, speeding up the upload and download process, and will prevent overwhelming the server when it is not in use.

To do this:
1. Open File Explorer to the location where you want the shortcuts (the desktop is a good choice).
2. Right-click in a blank space and select **New > Shortcut**.
3. Enter `\\frst-irsstor2\ByUser` as the location of the item.
4. Click **Next**.
5. Enter "ByUser" as the name for the shortcut.
6. Click **Finish**.

Follow the same steps for ByProject, replacing "ByUser" with "ByProject" in both the item location and the shortcut name.

You can now access these shares by opening the shortcuts.

### Moving Files To/From Network
To move files to or from the network shares, you **must** use the following robocopy command:

`robocopy <SOURCE> <DESTINATION> /XA:SH /E /MT:5 /ZB`


**Command details:**
- **robocopy**: The command itself, indicating that you want to use the Robocopy utility.
- **`<SOURCE>`**: The source directory or path. Replace `<SOURCE>` with the actual path (e.g., "P:/") of the directory you want to copy from (e.g., "\\frst-irsstor2\ByProject\_CanadaLayers\Rasters\DEM").
- **`<DESTINATION>`**: The destination directory or path. Replace `<DESTINATION>` with the actual path (e.g., "O:/") of the directory you want to copy to (e.g., "\\frst-irsstor2\ByUser\MurrayBrent").
- **/XA:SH**: Excludes files with the "System" and "Hidden" attributes from being copied.
- **/E**: Copies subdirectories, including empty ones.
- **/MT:5**: Enables multi-threaded copying using 5 threads (the default is 8).
- **/ZB**: Uses restartable mode, allowing the copy to resume if interrupted.

*Note: These network shares are for storing data only. DO NOT work directly off these shares; copy the files you need to your local machine and process your data locally.*

### Additional Notes
On the second Tuesday night of every month, the network shares will be rebooted. This reboot removes any lock files that may accumulate on the network when files are accessed directly rather than being copied locally. Please do not copy any files during this time, as doing so may result in corrupted files or missing data.

---
