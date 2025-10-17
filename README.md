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
