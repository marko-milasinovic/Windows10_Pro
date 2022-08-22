<h2 align="center"> Windows 10 Pro x64 first setup </h2> 

<h3 align="center"> A checklist for a complete first time setup </h3>

<p align="center">
<img src="https://img.shields.io/badge/Support-Windows%20x64-blue?logo=Windows&style=flat-square">
<img src="https://img.shields.io/github/license/marko-milasinovic/Windows10_LTSC?style=flat-square">
</p>

# Requirements
OS: Windows 10 installed onto 8GiB USB by [Microsoft Media Creaton tool](https://go.microsoft.com/fwlink/?LinkId=691209)

USB drive with at least 8GiB, final image file size on flash drive is ~4.8 GiB.

##### Table of Contents


<small><i><a href='http://ecotrust-canada.github.io/markdown-toc/'>Table of contents generated with markdown-toc</a></i></small>

## Windows system alterations
* Start > Edit Power Plan > Select High performance > Change plan settings > Change advanced power settings > Processor power management > Maximum processor state: 99%
  * File explorer Address bar: Navigate to Power options > Left side menu: Choose what the power buttons do > Change settings that are currently unavailable > Disable: Turn on fast startup; Enable sleep.
* View Advanced System Settings > Performance: Settings > Visual Effects > Select: Show windows content while dragging, Smooth edges of screen fonts
  * Advanced > Automatically manage=DISABLE > Page file size: Initial=1024, Maximum=8192
* regedit change for auto login functionality ??
* Automatically hide scroll bars in windows -> Uncheck

### Registry
Disable windows update in Registry (Set "start"=4)
* HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WaaSMedicSvc
* HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Wuaserv
* HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\windefend ?


Tools:
* [NirSoft](https://www.nirsoft.net/) (FOSS) - Registry tools

### Services
CMD: REGEDIT > HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services
* [Fax] Fax - Enables you to send and receive faxes, utilizing fax resources available on this computer or on the network
* [MapsBroker] Downloaded Maps Manager - application access to downloaded maps
* [DiagTrack] Connected User Experiences and Telemetry
* [CscService] Offline Files - performs maintenance activities on the Offline Files cache
* [PhoneSvc] Phone Service - Manages the telephony
* [RetailDemo] Retail Demo Service
* [wisvc] Windows Insider Service - infrastructure support for the Windows Insider Program
* [SmsRouter] Microsoft Windows SMS Router Service
* [XboxGipSvc] Xbox Accessory Management Service
* [XblAuthManager] Xbox Live Auth Manager
* [XboxNetApiSvc] Xbox Live Networking Service
* [XblGameSave] Xbox Live Game Save
* [lfsvc] Geolocation Service
* [irmon] Infrared monitor service


### Group policy
Search > Edit group policy
[admx GP wiki](https://admx.help/?Category=Windows_10_2016&Policy=Microsoft.Policies.ControlPanel::ForceClassicControlPanel) - Wiki for all group policy options
Administrative Templates (Computers):
* Configure Automatic Updates = DISABLED | Software\Policies\Microsoft\Windows\WindowsUpdate\AU
* Allow Automatic Updates immediate installation = DISABLED | Software\Policies\Microsoft\Windows\WindowsUpdate\AU

### Firewall changes
Search > Windows Defender Firewall > Advanced Settings > 
Disable firewall rule for:
* Work or shool account
* Wi-FI Direct network discovery
* Wi-FI Direct Scan
* Wi-FI Direct Spooler
* Microsoft Lync (Inbound)
* Microsoft Lync UcMapi (Inbound)
* Microsoft family features (outbound)

### Turn Windows Features on or off
Disable the following:
* Internet Explorer 11
* Work Folders Client

Enable the following:
* Hyper-V
* NET Framework 3.X
* NET Framework 4.X

## Task Scheduler
* Task Scheduler > Disable Edge

# Program list
Abbreviations: 
* FOSS - Free and Open-Source Software
* Freeware - software, most often proprietary, that is distributed at no monetary cost to the end user
* Shareware - proprietary software which has trial use at little or no cost with usually limited functionality, but which can be upgraded upon payment

## DefaultApplications
* [Chocolatey](https://chocolatey.org/install) (FOSS) - software management solution
```
    Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```
* [MPV - github](https://github.com/mpv-player/mpv) (FOSS) - optimised and simple media player
  * [MPV - chocolatey](https://community.chocolatey.org/packages/mpv) 
```
choco install mpv
```
* [Ruby - chocolatey](https://community.chocolatey.org/packages/ruby) 
```
choco install ruby
```
* [ffmpeg](https://ffmpeg.org/download.html) (FOSS) - command line multimedia framework (a complete, cross-platform solution to record, convert and stream audio and video)
```
choco install ffmpeg
```
* [MKVToolNix](https://mkvtoolnix.download/downloads.html#windows) (FOSS) - gui for working with Matroska files [gitlab](https://gitlab.com/mbunkus/mkvtoolnix)
```
choco install mkvtoolnix
```


* [Clementine](https://github.com/clementine-player/Clementine/releases/latest) (FOSS) - a "winamp" style music player
* [Greenshot](https://getgreenshot.org/downloads) (FOSS) - A screenshot tool, to use press "Prt Scr"
* [qimgv](https://github.com/easymodo/qimgv/releases/latest) (FOSS) - Image viewer
* [KeePass 2](https://keepass.info/download.html) (FOSS) - light-weight password manager
* [Notepad++](https://github.com/notepad-plus-plus/notepad-plus-plus/releases/latest) (FOSS) - multifunctional code/text editor
* [Revo Uninstaller](https://www.revouninstaller.com/start-freeware-download/) (Shareware) - advanced program uninstaller
* [7-zip with Zstandard](https://github.com/mcmilk/7-Zip-zstd/releases/latest) - file archiver with additional functions (eg. hash verification)


* [Adobe Reader](https://get.adobe.com/reader/download?os=Windows+10&name=Reader+DC+2022.002.20191+English+Windows%2864Bit%29&lang=en&nativeOs=Windows+10&accepted=&declined=mss%2Cmsc%2Ccr&preInstalled=&site=otherversions) (Freeware) - Propriatery pdf reader
  * Disable update service after install

### Browsers
* [Chrome](https://www.google.com/chrome/) (Freeware) - made by Google, based on the Chromium engine
* [Vivaldi](https://vivaldi.com/download/) (Freeware) - customisable browser, based on the Chromium engine

#### Browser extensions
* [UBlock Origin](https://github.com/gorhill/uBlock) (FOSS) - An efficient (ad) blocker for Chromium and Firefox
* [HTTPS Everywhere](https://www.eff.org/https-everywhere/) (FOSS) - encrypts your communications with many major websites
* [ClearUrls](https://gitlab.com/KevinRoebert/ClearUrls) (FOSS) - based on the new WebExtensions technology, automatically removes tracking elements from URLs

## Intel drivers
* [Intel's gpu driver](https://www.intel.com/content/www/us/en/support/products/80939/graphics.html) (Freeware) - For the specific gpu line

## File transfer
* [FileZilla](https://filezilla-project.org/) 

## Programming
* [Anaconda3](https://www.anaconda.com/products/individual) - package / environment manager,  Python3 distribution with 1,500+ open source packages
* [VirtualBox](https://www.virtualbox.org/wiki/Downloads) - x86 AMD64/Intel64 full virtualization
* [Visual Studio Code](https://github.com/VSCodium/vscodium/releases/latest) (FOSS) - JavaScript, TypeScript, Node.js (C++, C#, Java, Python, PHP, Go, .NET, Unity)
* [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) (FOSS ?) - SSH, Telnet, and SFTP client, typically used for remote access to server computers over a network using the SSH protocol along with an xterm terminal emulator
* [ImDIsk](https://www.ltr-data.se/opencode.html/#ImDisk) (FOSS) - virtual disk driver


## Utilities
* [DeepL](https://appdownload.deepl.com/windows/0install/DeepLSetup.exe) (Freeware) - Auto translate tool
* [Freeplane](https://github.com/freeplane/freeplane/releases) (FOSS) - Tools for mind mapping
* [PowerToys](https://docs.microsoft.com/en-us/windows/powertoys/install) (Microsoft) - Usefull windows tools
* [HWmonitor](https://www.cpuid.com/softwares/hwmonitor.html) (Shareware) - general purpose hardware monitoring program


### File Explorer
* Go to the Last Active window with a single click / Switch to last opened window
> Computer\HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced
> Right-click on Advanced> New> DWORD (32-bit) Value. Rename it to LastActiveClick
> Double click on LastActiveClick and change its value to 1

======
> HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced
> Advanced entry is selected, right-click on the white space in the right panel and select New > DWORD (32-bit) Value.
> LastActiveClick = 1

> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\MyComputer\NameSpace
> HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Explorer\MyComputer\NameSpace
> add minus infront of -{0DB7E03F-FC29-4DC6-9020-FF41B59E513A}

* Disable Action Center (Optional)
> Computer\HKEY_CURRENT_USER\Software\Policies\Microsoft\Windows
> Right-click on Windows> New> Key. Rename it to Explorer.
> Right-click on Explorer> New> DWORD (32-bit) Value. Rename it to DisableNotificationCenter.
> Double-click on DisableNotificationCenter and change the value to 1.

* [WinTweaker](https://www.thewindowsclub.com/ultimate-windows-tweaker-4-windows-10) (Freeware) - Windows settings tweaker

* Enable verbose status messages
> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System
> System entry and then right-click on the white space in the right panel and select New > DWORD (32-bit) Value.
> verbosestatus = 1

* Apps in the context menu [GeekFlare](https://geekflare.com/windows-11-registry-tweak/)
> HKEY_CLASSES_ROOT\Directory\Background\shell


### Windows services
Start Menu > Services > Windows Update > Disable the following:
* autotimesvc
* DiagTrack
* dmwappushservice
* FrameServer
* icssvc
* InstallService
* MapsBroker
* PhoneSvc
* RasMan
* RemoteAccess
* RemoteRegistry
* SessionEnv
* SysMain ?
* UevAgentService
* UmRdpService
* WalletService
* WbioSrvc
* wisvc
* WMPNetworkSvc
* WpcMonSvc
* WSearch
* ALG ?
* AppReadiness ?
* BITS
* Microsoft (R) Diagnostics Hub Standard Collector Service (diagnosticshub.standardcollector.service)
* Enterprise App Management Service (EntAppSvc)
* MicrosoftEdgeElevationService
* MixedRealityOpenXRSvc
* Windows Perception Simulation Service (perceptionsimulation)
* Performance Logs & Alerts (pla)
* RetailDemo
* Windows Backup (SDRSVC)
* Radio Management Service (RmSvc)
* Spatial Data Service (SharedRealitySvc)
* Smart Card Removal Policy (SCPolicySvc)
* Microsoft Storage Spaces SMP (smphost)
* ??? Windows Defender Advanced Threat Protection Service (Sense)
* Microsoft Software Shadow Copy Provider (swprv)
* Telephony (TapiSrv)
* Remote Desktop Services (TermService)
* ?????? Web Account Manager (TokenBroker)
* Volume Shadow Copy (VSS)
* Windows Update Medic Service (WaaSMedicSvc) 
//added in update 1803 
//Computer Configuration \ Preferences \ Windows Settings \ Registry 
//HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WaaSMedicSvc
//value name is Start and please set the value to 4.
// Source [technet](https://social.technet.microsoft.com/Forums/en-US/8706fda2-f7cd-4dab-814b-72283b17c423/how-to-disable-windows-update-medic-service)
* BitLocker Drive Encryption Service (BDESVC)
* Offline Files (CscService)
* Microsoft Edge Update Service (edgeupdatem)
* IP Translation Configuration Service (IpxlatCfgSvc)
* Geolocation Service (lfsvc)
* Microsoft Passport (NgcSvc)
* Microsoft Passport Container (NgcCtnrSvc)
* Windows PushToInstall Service (PushToInstall)
* Microsoft Windows SMS Router Service (SmsRouter)
* Windows Perception Service (spectrum)
* Touch Keyboard and Handwriting Panel Service (TabletInputService)
* Microsoft Account Sign-in Assistant (wlidsvc)
* Windows Update (wuauserv)


### Optional
* [Waifu2x Caffe](https://github.com/lltcggie/waifu2x-caffe/releases/latest) (FOSS) - image denoiser & upscaler (slow, best used with Nvidia GPU's)
* [Waifu2x Extension GUI](https://github.com/AaronFeng753/Waifu2x-Extension-GUI/releases/latest) video & image denoiser & upscaler with multiple algorithms
* [other_video_transcoding](https://github.com/donmelton/other_video_transcoding) (FOSS) - highly efficient transcoding cli for h.264 to h.265
* [Dandere2x](https://github.com/akai-katto/dandere2x/releases/latest) (FOSS) - efficient video upscaler that uses waifu2x and video compression technology


<hr>
