@echo off
setlocal
chcp 65001 >nul

:: تحديد مكان النسخ الاحتياطي (تغيّر حرف الفلاشة حسب جهازك)
set "usbdrive=E:"
set "backupfolder=%usbdrive%\TestBackup"

:: تحديد المسارات
set "desktop=%userprofile%\Desktop"
set "pictures=%userprofile%\Pictures"
set "documents=%userprofile%\Documents"
set "favorites=%userprofile%\Favorites"
set "recent=%appdata%\Microsoft\Windows\Recent"

:: إنشاء مجلد النسخ الاحتياطي
echo Creating backup folder: %backupfolder%
mkdir "%backupfolder%" >nul 2>&1

:: ====== نسخ سطح المكتب ======
if exist "%desktop%" (
    echo [+] Copying Desktop...
    xcopy "%desktop%\*" "%backupfolder%\Desktop\" /s /e /h /i /q
)

:: ====== نسخ الصور ======
if exist "%pictures%" (
    echo [+] Copying Pictures...
    xcopy "%pictures%\*" "%backupfolder%\Pictures\" /s /e /h /i /q
)

:: ====== نسخ المستندات ======
if exist "%documents%" (
    echo [+] Copying Documents...
    xcopy "%documents%\*" "%backupfolder%\Documents\" /s /e /h /i /q
)

:: ====== نسخ المفضلات ======
if exist "%favorites%" (
    echo [+] Copying Favorites...
    xcopy "%favorites%\*" "%backupfolder%\Favorites\" /s /e /h /i /q
)

:: ====== نسخ الملفات الأخيرة ======
if exist "%recent%" (
    echo [+] Copying Recent Files...
    xcopy "%recent%\*" "%backupfolder%\Recent\" /s /e /h /i /q
)

echo.
echo ✅ Backup completed successfully!
pause
