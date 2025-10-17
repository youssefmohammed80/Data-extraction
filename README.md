# USB Backup Tool

A batch script for backing up user data to a USB drive. This tool automatically copies common user folders to a backup location on removable storage.

## ⚠️ Disclaimer
**Use this tool responsibly and only on computers you own or have permission to access.** Unauthorized data copying may violate privacy laws and regulations.

## Features
- Backs up Desktop, Pictures, Documents, Favorites, and Recent files
- Simple batch script implementation
- Automatic folder creation
- Silent operation with progress indicators

## Code

```batch
@echo off
setlocal
chcp 65001 >nul

:: Set USB drive location (change drive letter according to your system)
set "usbdrive=E:"
set "backupfolder=%usbdrive%\TestBackup"

:: Define paths
set "desktop=%userprofile%\Desktop"
set "pictures=%userprofile%\Pictures"
set "documents=%userprofile%\Documents"
set "favorites=%userprofile%\Favorites"
set "recent=%appdata%\Microsoft\Windows\Recent"

:: Create backup folder
echo Creating backup folder: %backupfolder%
mkdir "%backupfolder%" >nul 2>&1

:: ====== Copy Desktop ======
if exist "%desktop%" (
    echo [+] Copying Desktop...
    xcopy "%desktop%\*" "%backupfolder%\Desktop\" /s /e /h /i /q
)

:: ====== Copy Pictures ======
if exist "%pictures%" (
    echo [+] Copying Pictures...
    xcopy "%pictures%\*" "%backupfolder%\Pictures\" /s /e /h /i /q
)

:: ====== Copy Documents ======
if exist "%documents%" (
    echo [+] Copying Documents...
    xcopy "%documents%\*" "%backupfolder%\Documents\" /s /e /h /i /q
)

:: ====== Copy Favorites ======
if exist "%favorites%" (
    echo [+] Copying Favorites...
    xcopy "%favorites%\*" "%backupfolder%\Favorites\" /s /e /h /i /q
)

:: ====== Copy Recent Files ======
if exist "%recent%" (
    echo [+] Copying Recent Files...
    xcopy "%recent%\*" "%backupfolder%\Recent\" /s /e /h /i /q
)

echo.
echo ✅ Backup completed successfully!
pause

Usage Instructions
1. Configuration
Change the usbdrive variable to match your USB drive letter

Modify the backupfolder name if desired

2. Running the Script
Save as BackupTool.bat

Run as Administrator for best results

Insert USB drive before running

3. What Gets Backed Up
Desktop: All files and folders from desktop

Pictures: Entire Pictures library

Documents: All documents and subfolders

Favorites: Browser bookmarks (Internet Explorer/Edge)

Recent: Recently accessed files history

XCopy Parameters Explained
/s - Copy directories and subdirectories

/e - Copy empty directories

/h - Copy hidden and system files

/i - Assume destination is a directory

/q - Quiet mode (no file names)

🔒 Protection Guide
How to Prevent Unauthorized Backup
Physical Security

Don't leave computers unlocked

Use privacy screens in public

Enable automatic screen lock

USB Access Control

Disable USB ports via Group Policy

Use device control software

Monitor USB connection events

User Education

Be cautious of unknown USB devices

Don't run unknown batch files

Regularly check connected devices

System Monitoring

Enable file access auditing

Use security software

Monitor for large file transfers

Legal and Ethical Notice
This tool is intended for:

Personal backup purposes

Authorized IT administration

Educational cybersecurity research

Unauthorized use is illegal. Always ensure you have proper permissions before accessing or copying data from any computer system.
