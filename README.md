# tiny1123h2builder

Scripts to build a trimmed-down Windows 11 23H2 image.

This is a script to automate the build of a streamlined Windows 11 23H2 image, similar to tiny11 23h2.
My main goal is to use only Microsoft utilities like DISM, and nothing external. The only executable included is oscdimg.exe, which is provided in the Windows ADK and it is used to create bootable ISO images. Also included is an unattended answer file, which is used to bypass the MS account on OOBE and to deploy the image with the /compact flag.
It's open-source, so feel free to add or remove anything you want! Feedback is also much appreciated.

Warning: Only build 22631.2361 (latest Insider build Release Preview channel as of now) are supported.

Instructions:

1. Download Windows 11 build 22631.2361 (latest Insider build Release Preview channel as of now) from UUPdump or Microsoft website (<https://www.microsoft.com/software-download/windows11>)
2. Mount the downloaded ISO image using Windows Explorer.
3. After you mount the downloaded ISO image, run tiny11 23h2 creator.bat as administrator.
4. Select the drive letter where the image is mounted (only the letter, no colon (:))
5. Select the SKU that you want the image to be based.
6. Sit back and relax :)
7. When the image is completed, you will see it in the folder where the script was extracted, with the name tiny11 23h2.iso

What is removed:
Clipchamp,
News,
Weather,
GetHelp,
GetStarted (Tips),
Office Hub,
Solitaire,
PeopleApp,
PowerAutomate,
ToDo,
Alarms,
Mail and Calendar,
Feedback Hub,
Maps,
Sound Recorder,
Your Phone,
QuickAssist,
Internet Explorer,
LA57 support,
OCR for en-us,
Speech support,
TTS for en-us,
Media Player Legacy,
Tablet PC Math,
OneDrive,
WindowsCamera,
Microsoft Teams

Known issues:

1. The script is rather inflexible, as in only the builds specified can be modified. This is because with each new build Microsoft also updates the inbox apps included. If one tries to use other builds, it will work with varying degrees of success, but some things like the removal of Edge and OneDrive as well as bypassing system requirements or other patches will always be applied.
2. Only en-us x64 is supported as of now. This can be easily fixable by the end user, just by replacing every instance of en-us with the language needed (like ro-RO and so on), and every x64 instance with arm64.
3. This builder it still have few UWP apps, so you have to use NTLite to remove the UWP apps for maximum 27 apps on this part What is removed on README.md
4. If you want to run this builder but with another build, you go to tiny11 23h2 creator, right button, show more option and edit, you scroll down to echo Removing Internet Explorer...
dism /image:c:\scratchdir /Remove-Package /PackageName:Microsoft-Windows-InternetExplorer-Optional-Package~31bf3856ad364e35~amd64~en-US~11.0.xxxxx.xxxx > nul
echo Removing LA57:
dism /image:c:\scratchdir /Remove-Package /PackageName:Microsoft-Windows-Kernel-LA57-FoD-Package~31bf3856ad364e35~amd64~~10.0.xxxxx.xxxx > nul
echo Removing Handwriting:
dism /image:c:\scratchdir /Remove-Package /PackageName:Microsoft-Windows-LanguageFeatures-Handwriting-en-us-Package~31bf3856ad364e35~amd64~~10.0.xxxxx.xxxx > nul
echo Removing OCR:
dism /image:c:\scratchdir /Remove-Package /PackageName:Microsoft-Windows-LanguageFeatures-OCR-en-us-Package~31bf3856ad364e35~amd64~~10.0.xxxxx.xxxx > nul
echo Removing Speech:
dism /image:c:\scratchdir /Remove-Package /PackageName:Microsoft-Windows-LanguageFeatures-Speech-en-us-Package~31bf3856ad364e35~amd64~~10.0.xxxxx.xxxx > nul
echo Removing TTS:
dism /image:c:\scratchdir /Remove-Package /PackageName:Microsoft-Windows-LanguageFeatures-TextToSpeech-en-us-Package~31bf3856ad364e35~amd64~~10.0.xxxxx.xxxx > nul
echo Removing Media Player Legacy:
dism /image:c:\scratchdir /Remove-Package /PackageName:Microsoft-Windows-MediaPlayer-Package~31bf3856ad364e35~amd64~~10.0.xxxxx.xxxx > nul
dism /image:c:\scratchdir /Remove-Package /PackageName:Microsoft-Windows-MediaPlayer-Package~31bf3856ad364e35~wow64~en-US~10.0.xxxxx.xxxx > nul
dism /image:c:\scratchdir /Remove-Package /PackageName:Microsoft-Windows-MediaPlayer-Package~31bf3856ad364e35~amd64~~10.0.xxxxx.xxxx > nul
dism /image:c:\scratchdir /Remove-Package /PackageName:Microsoft-Windows-MediaPlayer-Package~31bf3856ad364e35~wow64~~10.0.xxxxx.xxxx > nul
echo Removing Tablet PC Math:
dism /image:c:\scratchdir /Remove-Package /PackageName:Microsoft-Windows-TabletPCMath-Package~31bf3856ad364e35~amd64~~10.0.xxxxx.xxxx > nul and change build to any build you want (it just supported for Windows Insider Preview for all channel)
Example:
echo Removing Internet Explorer...
dism /image:c:\scratchdir /Remove-Package /PackageName:Microsoft-Windows-InternetExplorer-Optional-Package~31bf3856ad364e35~amd64~en-US~11.0.25951.1010 > nul
echo Removing LA57:
dism /image:c:\scratchdir /Remove-Package /PackageName:Microsoft-Windows-Kernel-LA57-FoD-Package~31bf3856ad364e35~amd64~~10.0.25951.1010 > nul
echo Removing Handwriting:
dism /image:c:\scratchdir /Remove-Package /PackageName:Microsoft-Windows-LanguageFeatures-Handwriting-en-us-Package~31bf3856ad364e35~amd64~~10.0.25951.1010 > nul
echo Removing OCR:
dism /image:c:\scratchdir /Remove-Package /PackageName:Microsoft-Windows-LanguageFeatures-OCR-en-us-Package~31bf3856ad364e35~amd64~~10.0.25951.1010 > nul
echo Removing Speech:
dism /image:c:\scratchdir /Remove-Package /PackageName:Microsoft-Windows-LanguageFeatures-Speech-en-us-Package~31bf3856ad364e35~amd64~~10.0.25951.1010 > nul
echo Removing TTS:
dism /image:c:\scratchdir /Remove-Package /PackageName:Microsoft-Windows-LanguageFeatures-TextToSpeech-en-us-Package~31bf3856ad364e35~amd64~~10.0.25951.1010 > nul
echo Removing Media Player Legacy:
dism /image:c:\scratchdir /Remove-Package /PackageName:Microsoft-Windows-MediaPlayer-Package~31bf3856ad364e35~amd64~~10.0.25951.1010 > nul
dism /image:c:\scratchdir /Remove-Package /PackageName:Microsoft-Windows-MediaPlayer-Package~31bf3856ad364e35~wow64~en-US~10.0.25951.1010 > nul
dism /image:c:\scratchdir /Remove-Package /PackageName:Microsoft-Windows-MediaPlayer-Package~31bf3856ad364e35~amd64~~10.0.25951.1010 > nul
dism /image:c:\scratchdir /Remove-Package /PackageName:Microsoft-Windows-MediaPlayer-Package~31bf3856ad364e35~wow64~~10.0.25951.1010 > nul
echo Removing Tablet PC Math:
dism /image:c:\scratchdir /Remove-Package /PackageName:Microsoft-Windows-TabletPCMath-Package~31bf3856ad364e35~amd64~~10.0.25951.1010 > nul

And that's pretty much it for now!
Thanks for trying it and let me know how you like it!
