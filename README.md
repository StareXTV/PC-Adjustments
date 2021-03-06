##### Performance & Latency Optimization & System tweaks - Provided by StareX

# What is this guide all about?

It's a handbook filled with **tweaks, system optimizations and performance & latency improvements** to achieve optimal performance and squeeze out every last bit of your hardware capabilities without harming them in an easy to read format.

# Getting to business, Windows 10 Setup + UEFI vs Legacy
> Disclaimer: You can skip this process, this is a **RECOMMENDED** process but it's not a **Mandatory** one.

## Installing Windows 10 Pro
The recommended method to install Windows 10 is via the Microsoft website, avoid downloading any Win10 downloads off torrents or other websites as they might contain malware.

[Download the Media Tool Creation](https://www.microsoft.com/en-us/software-download/windows10)
Press **Download tool now**, and run the installation media.

We recommend you use a USB Thumb drive and **format** it to **NTFS** and prepare it with the installation files, select to prepare a Windows 10 **Pro** 64bit - **We recommend running 64bit for users that have over 4GB of RAM, otherwise select 32bit if your processor doesn't support 64bit**

[What is the difference? 34bit vs 64bit](https://www.pcmag.com/news/32-bit-vs-64-bit-oses-whats-the-difference)

## Now wait for a second, why would I even read about Windows 10 setup in a performance guide?

Good question, If you bought your computer recently, you may have come across the word "UEFI" or "BIOS, Legacy". The main difference between **UEFI and Legacy** is the method of booting a computer, **UEFI (Using GUID Partition Table aka GPT)** is the latest method available and designed to replace BIOS and booting with the UEFI firmware, while **Legacy Boot (Using Master Boot Record)** is the process of booting the computer using BIOS firmware.

UEFI gradually replaces traditional BIOS on most PCs, it includes greater security features than legacy and also boots faster, and noticeable performance improvement.

## Check if you're on Legacy or UEFI

You can check if you're on Legacy or UEFI via **System Information**

Press your **Windows** button and **R** together, this window will open

![run window](https://i.imgur.com/BmiHrPb.png)

Type in: **msinfo32.exe**

Then look for **BIOS Mode**, there you'll see **UEFI** or **Legacy**.


## How to setup UEFI Boot up for Windows 10?

> Disclaimer: **You should not do this unless you're formatting your PC**, you can look up ways to convert a drive from MBR to GPT online, we won't be dwelling into this because of complications that may occur. **Do it at your own risk**

Read here: [Convert my drive](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/windows-setup-installing-using-the-mbr-or-gpt-partition-style)

When you restart/start your computer you will be greeted with your **Motherboard Splashscreen**
<img src="https://www.tonymacx86.com/attachments/camerazoom-20150316194843548-jpg.130619/" alt="Stuck on Gigabyte Startup Screen | tonymacx86.com" style="zoom:50%;" />

**Enter your BIOS, Pressing the DEL button OR F1, F2, F10, Esc, or in really older machines Ctrl+Alt+Esc or Ctrl+Alt+Delete**

* Make sure you have "CSM Support" (Stands for Compatibility Support Module) disabled
* Enter the **Boot** menu of your motherboard, there you'll see your USB thumb drive.
* Select "UEFI: USB Thumb drive name" and not something like "P1: USB Thumb drive name" as Boot Priority 1
* Save and Exit
* Install Windows 10 the traditional way
  * In the Installation, make sure you **Delete** the partition you want to install Windows on, recommended on an [SSD](https://www.youtube.com/watch?v=YQEjGKYXjw8)
  * Press "New" and set it to max capacity
  * Install Windows 10 on the largest partition that has been created and not System Reserved, MBR or Recovery partitions.
# After setting up Windows 10, Debloating & Programs

## Installing Programs that we want

After setting up our Windows 10, we can now go to a really handy dandy website called Ninite, this site will give us a plethora of programs updated to their latest version without installing them one by one, it'll do it all for us.

https://ninite.com/

## Debloating Windows 10 for smooth experience
> Recommended step for optimal performance

After that we can move on to debloating Windows 10 by running a few scripts, **This will debloat/remove programs like Overdrive, Windows Defender, optimize user interface, provide Mouse Fixes and other.**

https://github.com/W4RH4WK/Debloat-Windows-10

Make sure you press on Clone or download, then "Download ZIP"

![img](https://i.imgur.com/5VvoPal.png) 

Unzip what you download and place it in a convenient folder we can easily access, I recommend the Desktop.

```python
Run PowerShell as an admin
```

Look for the folder you unzipped, if you unzipped it on your Desktop then the syntax is:
![img](https://i.imgur.com/YtAsvys.png)

```bash
cd .. - Backs out of a folder 
```
```bash 
cd foldername - enters a foldername
```
```bash
ls - views the content of the folder
```

Enter the scripts folder by typing: cd .\scripts\ when inside the Debloat folder
Or type: 
```bash
cd C:\Windows\Users\YourUserName\Desktop\Debloat-Windows-10-master\scripts
```

Once inside the scripts folder, type the following:

```bash
PS > Set-ExecutionPolicy Unrestricted
```
```bash
PS > ls -Recurse *.ps1 | Unblock-File
```
```bash
PS > ls -Recurse *.psm1 | Unblock-File
```

type **ls** to see the list of the script files, you will see 9 script files, run all of them by typing .\scriptname, Hitting TAB will autocomplete the filename for you.
Example: .\disable-services.ps1

Run all 9 of them.

**DO NOT disable Overdrive if you use it**

**We're done! Debloat is complete, now I'd want to show you more ways you can do to optimize Windows 10**

## Oh wait, my modern metro looking volume slider is missing! what happened?

That's alright, it's because of the interface optimization script, we can revert these changes by going into the Regedit, it just replaced the modern look to the Windows 7 style slider.

Look in Windows Search for "Regedit or Registry", alternatively in the "Run" program, type in: **Regedit** and hit enter.

Go inside **HKEY_LOCAL_MACHINE -> SOFTWARE -> Microsoft -> Windows NT -> CurrentVersion -> MTCUVC**
In there you'll find "**EnableMtcUvc**" set to **0**, set it to **1** by changing the value and press OK, it will automatically revert you to the modern look of the volume slider.
![img](https://i.imgur.com/JBpI9hI.png)

## Important drivers, and latest ones
> Recommended step for optimal performance

Ever wondered where to get the latest Realtek driver or a WiFi driver, click here: https://www.station-drivers.com/

And you can look for them in here.

## Windows Privacy Settings Tweaks - Shutup 10!  Antispy Tool By O&O
> Recommended step for optimal performance

I don't like my OS sending information about what I do to an outside source, it doesn't matter to who or for what cause, luckily there are few ways to intercept this and disable telemetry and other background apps that run in that might run in the background from Windows 10.

Luckily there's a handy tool that does it all for us, and we don't need to go into the "Windows Privacy" settings and manually toggle sliders on or off, it does it all for us.

**Go and download:** https://www.oo-software.com/en/shutup10

It's NOT an installer, place this file somewhere safe, and don't delete it, it **benefits you**, it's not malware.
When you enter the program, go to Actions and Apply their **recommended settings**
<img src="https://i.imgur.com/f1cYXX6.png" alt="img" style="zoom:60%;" />

You can toy around with this software, it's pretty cool!



## Moving on, NVIDIA/AMD Drivers - Important
> Recommended and probably a Mandatory step for optimal performance

The next step is to **correctly** install NVIDIA/AMD drivers.

Install the latest version of [Display Driver Uninstaller](https://www.guru3d.com/files-details/display-driver-uninstaller-download.html) in The Guru3D website.

We need to do this part because Windows update installs a very old driver, uninstalling it via DDU will ensure that we will run our drivers optimally.

Open DDU, Options -> Make sure to tick the highlighted like in this screenshot
![img](https://i.imgur.com/OiO32a2.png)

After that, select GPU as Device, and select AMD or NVIDIA.

Hit **Clean and Restart**

Afterward, Download latest NVIDIA drivers from here, and use "Standard" and not "DCH":
https://www.nvidia.com/Download/Find.aspx

AMD:
https://www.amd.com/en/support



# SYSTEM Optimizations
> Recommended steps for optimal performance, read through everything in order.

The system optimization section is where it's all about, from troubleshooting and solving "Out of Memory" errors, to system instabilities, to unparking your CPU cores, and a few other tweaks and fixes.

## msi Mode
> Super Recommended step for optimal performance!

Not to be confused with the company MSI, MSI stands for "**M**essage **S**ignaled-Based **I**nterrupts".
The MSI mode allows your PCI devices to communicate better with your CPU and vice versa such as your GPU.
We are strictly going to talk about your GPU now because this is what we'd want to improve the latency on.

You can read more about it in Guru3D Forums, explained by a user named mbk1969 [msi vs line-based](https://forums.guru3d.com/threads/windows-line-based-vs-message-signaled-based-interrupts-msi-tool.378044/)

**Download MSI Utility:** http://www.mediafire.com/file/2kkkvko7e75opce/MSI_util_v2.zip

* Unzip it and run it as an Admin.
![img](https://i.imgur.com/I89pb2J.png)

* Look for your GPU, for you it'll be unticked and the IRQ will be a positive number. Make sure the "Supported Modes" is "LineBased, Msi". **Tick the GPU** and set interrupt priority on **High.**

Restart your PC and you're done. To validate if you are running MSI mode on your GPU, open the program again and see if IRQ is in a negative number or a different number than what it was previously.

## AntiVirus
I recommend against using Antivirus software as it impacts over around 3% performance loss such as launching apps and boot times, More in [LinusTechTips video](https://www.youtube.com/watch?v=pzeKPiwEfXk) explaining and showing benchmarks.

To uninstall any Antivirus software you have, I will provide you with a solution that will disinfect and clean up your PC thoroughly without having to worry about having an Antivirus in the background tempering with our PC.

## Disabling High Precision Event Timer
> Recommended step for optimal performance

Open CMD as an admin and type

```bash
bcdedit /deletevalue useplatformclock
```
If it doesn't work then:
```bash
bcdedit /set useplatformclock false
```
You can confirm it by typing in CMD and look for useplatformclock:
```bash
bcdedit /enum
```
* Press **Windows Key + R** together launching the Run program, and type in **devmgmt.msc**
  * Inside Device Manager click on "View" and look for **Devices by connection**
  * Click "View" again and click on **Show Hidden Devices** 
  * Look for **High precision event timer** in the Devices list
  * Once you find HPET, Disable the device, for me it was inside **Microsoft ACPI-Compliant System -> PCI Express Root Complex**
  
Every system is different so enabling or disabling will maybe help or not change anything at all, it's said that if you have an older CPU, then it might not benefit you to disable it, if you own a very fast CPU then you might see 10fps or more improvement when it's disabled.

**You must reboot after applying this setting, but can continue with ISLC down below**

## Intelligent Standby List Cleaner - Helps reduce stuttering in games
> Recommended step for optimal performance

This will improve latency and memory allocation, it's designed to clean standby RAM that is gathered throughout a gaming or program session, we can clean this standby list to free up RAM, this will help reduce stuttering in games.

* Open CMD as an Admin and type:
```bash
bcdedit /set useplatformtick yes
```
  * Download and unzip this: 
https://www.wagnardsoft.com/forums/viewtopic.php?t=1256

* Open ISLC and tick both "**Start ISLC Minimized**" and "**Launch ISLC on user logon**" and "**Enable custom timer resolution**"
* Set the **Wanted timer resolution** to **0.50**, Set **ISLC polling Rate** (ms) to **1000**
* Set **The list size is at least:** 1024 MB
* Set **Free memory is lower than**: Divide your memory by 2
  * 4GB is 4096 so lower than **2048**
  * 8GB is 8192 so lower than **4096**
  * 16GB is 16384 so lower than **8192**
* Click "**Start**" and minimize it, let it run in the background and do its thing.

**Should look like this at the end.**
![img](https://i.imgur.com/AXdU89H.png)
**You must reboot after applying this setting to achieve the 0.5ms Current and Maximum timer resolution**.

## CPU Un-parking - Bitsum Park Control (Not recommended for laptops as this will use more energy)
> Recommended step for optimal performance

Unparks your CPU so you'll use more of it than half of it as Windows is parking cores to save in energy, this decreases performance and we don't want that. You can comfortably use their **Bitsum High-Performance** configuration inside the program.

* Download here: https://bitsum.com/parkcontrol/
![img](https://i.imgur.com/lEr0wqo.png)

* Set Parking AC as Disabled and at 100%
* Set Parking DC as Disabled and at 100%
* Set Freq Scaling AC as Disabled at 100%
* Set Freq Scaling DC as Disabled at 100%
Hit "Apply" when doing changes and "Make Active" to apply the power plan.

## Windows 10 Game Mode
> Not Recommended step for optimal performance

Microsoft introduced "Game Mode" with Windows 10 creators update, which is meant to help optimize your PC's gaming performance, you can use it if you don't want to be bothered by anything Windows-related like Windows Update (even though we tweaked it when applying the Debloater scripts)

Though, it has been reported in various places that this optimization can be hurt performance in games and Twitch Streaming (OBS, Xsplit, Streamlabs) and cause fps drops during sessions.

**Disable it to gain stability**
<img src="https://i.imgur.com/o9QataP.png" alt="img" style="zoom:50%;" />

## NVIDIA Inspector and CUDA P2 State (For NVIDIA Only)
> Recommended step for optimal performance and VISUAL corrections!

NVIDIA Inspector is an application that reads out driver and hardware information for NVIDIA cards, it also allows you to tinker with settings that are not present in the NVIDIA Control Panel.

What we are going to do in this section is disable CUDA P2 State, it's practically a Power saving feature for CUDA compute workloads for rendering, deep learning, mining, etc. **In result, it lowers memory clock accordingly** to save on energy, this causes instability in some cases.

* Download it from here: https://github.com/Orbmu2k/nvidiaProfileInspector/releases
* Once downloaded, unzip the file somewhere in your computer and launch the program as an Admin.
You'll be greeted with a bunch of settings, some of them will be familiar for you as it draws the data from your 3D Managed Settings, but with greater control.
I'm not going to go through every single function and what it does but only what I found that is worth enabling and disabling to provide a smooth experience.

**If you have OC'd your memory, do it from scratch because after doing this modification your compute workloads will use the maximum memory clock from the P0 State.**

#### Disabling CUDA P2 State
* Scroll down to "Common"
* Find "CUDA - Force P2 State" and turn it off.
![img](https://i.imgur.com/zMEmqJn.png)

Additional settings that might help with Visuals and performance are the following:

#### For GSYNC / Freesync / Adaptive Sync users:

* **Frame Rate Limiter Mode:** Limiter V2 - Force Off [Enables Limiter V1 (Less Input Lag)]
* **GSYNC - Application Mode**: Fullscreen Only
* **GSYNC - Application State**: Allow
* **GSYNC - Global Feature**: On
* **GSYNC - Global Mode**: Fullscreen Only
* **Prefered Refreshrate**: Highest Available
* **Vertical Sync**: Force on
* **Anisotropic filtering mode** - User-defined / Off
* **Anisotropic filtering setting** - 16x
* **Power Management Mode** - Prefer Maximum Performance
* **Threaded Optimization** - On
  * Make sure to go into your NVIDIA Control Panel and enable "Low Latency Mode" to Ultra after applying these changes.
* After applying these settings make sure you have also enabled an FPS Limiter -3 off your Refresh Rate.
* So if you have a 144Hz GSYNC Display put 141fps in your limiter. (Riva-Tuner Statistics Server is recommended)
More on that here: https://blurbusters.com/gsync/gsync101-input-lag-tests-and-settings/

#### For non-GSYNC/Adaptive sync/Freesync users:

* **Frame Rate Limiter Mode:** Limiter V2 - Force Off [Enables Limiter V1 (Less Input Lag)]
* **Prefered Refreshrate**: Highest Available
* **Vertical Sync**: Force off
* **Anisotropic filtering mode** - User-defined / Off
* **Anisotropic filtering setting** - 16x
* **Power Management Mode** - Prefer Maximum Performance
* **Threaded Optimization** - On

After you're done applying these settings, hit "Apply Changes" at the top right corner, and save the profile (You'll see an icon of an arrow pointing upwards, click on "Export Profile" and save it where you can Import it when you update your drivers)

## Setting Affinity for NVIDIA Drivers to improve latency
> Recommended step for LATENCY performance! It really helps :D

Windows uses almost every driver including GPU drivers to Core 0 on your computer, you can gradually improve latency making your mouse and tasks feel snappier by assigning your GPU to the 4th Core if you have an 8 cores system, or to the 4th core if you have a 4 cores system, or if you have 8 and 16 threads core system then the 5th core (8 and 9).

I own an 8 Core and 16 Threads CPU

Download Here: https://drive.google.com/file/d/11wY-o8Q8SB1awuQWjHamC7uJMLH63tr2/view

* Run the Interrupt Affinity Policy Tool as an Admin
* Look for your NVIDIA card, you'll be met with an error so ignore it.
* Press "Set Mask", and you'll see "Core 0 1 2 3 4 5 6 7 8" etc, I set it to 8 and 9.
  * Core 0 & 1 are the first **core**
  * Core 2 and 3 are the **2nd core**
  * Core 4 and 5 are the **3rd core**
  * Core 6 and 7 are the **4th core**
  * Core 8 and 9 are the **5th core** and so on
  (**IF Hyper-Threading is Enabled, if Disabled then Core 0 is 1, Core 1 is 2 and etc**)
* It will ask you to restart your device, press OK, your monitor will go black and then you'll see your screen again.

**This alone improved my latency by a lot!**

## Enabling XMP Profile
> Recommended step for optimal performance! Reduces stuttering in games

XMP stands for "Extreme Memory Profiles", it's an Intel technology that allows you to change the memory settings to the manufacturer Overclocked settings to run your RAM at its optimal performance.

It can solve slowdowns, give you more FPS and it's a setting that many forget to enable, so why not?

For your information, DDR4 default values are **2133MHz**, whereas oftentimes you'd buy RAM sticks that are 3200MHz, ever wondered why you're stuttering and missing frames? That's probably why. RAM speed also benefits Ryzen CPUs.

To Enable XMP profile go into your BIOS settings and inside your Memory Settings look for "XMP Profile" or "Memory Profile".
![How to Enable Intel XMP to Make Your RAM Run at Its Advertised Speeds](https://www.howtogeek.com/wp-content/uploads/2016/06/xmp-bios-marked-650x392.png)

And you're done! Save and Exit :)

## Pagefile setup - Helps with "Running out of Memory"
> Recommended step for optimal performance

To put it short, it's a way to provide your computer to perform smoothly by reducing the workload of the physical memory, so at times when you have "running out of memory", then it's maybe because of Pagefile, you can read more about it online but we're going to just simplify it.

If you have an SSD and an HDD or SSD with an SSD, make sure Local C is set to "System Managed" and your HDD to "No Paging file"

* Right-click on "This PC" and then "Properties"
* Press on "Advanced System Settings" and then "Advanced"
* Under "Performance" click on "Settings"

![img](https://i.imgur.com/sJbALXM.png)
* After you're inside Performance options, click on "Advanced" again and then "Virtual Memory"

![img](https://i.imgur.com/o890eLm.png)

* Untick "**Automatically manage paging file size for all drivers**"
* set your **SSD Main drive** or HDD to **System Managed**
* Set your Gaming drive to **No paging file**.
* Press OK, and restart your PC to take effect.

## TRONScript
> Not a Recommended step for optimal performance but useful!

First of all, I fell in love with this project and all credits to its makers, you can read about it more in their Reddit page here:

https://www.reddit.com/r/TronScript/comments/g80580/tron_v1110_20200425_remove_malwarebytes/

Alongside with the download link and how to run it.

It debloats, cleans your deepest temp files, it **Disinfects** which is what I told you guys about in the AntiVirus section above as it runs 4 different antivirus and antimalware software that scans your PC for any malicious files and cleanses it out, it repairs your system and overall makes your PC cleaned out.

Sounds good? **Remember, running it will take time when it starts you need to leave your PC alone and let Tron do its thing, don't interrupt it. the logs will be stored inside your C drive.**



## Startup Programs - Helps with booting times
> Recommended step for BOOT times

Yeah, you could go inside your Task Manager and then "Startup" and disable all startup programs that you don't need, but there are also a few regedit settings you can do, as an Advanced to cease startup programs that might not appear in the "Startup" tab of Task Manager.

> **Remember to EXPORT your regedit BEFORE changing these settings to revert mistakes, Click on "File" and then Export**

Startup Contains inside:

Computer\HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run
Computer\HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\RunOnce
Computer\HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\StartupApproved
Computer\HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\StartupApproved\Run

Also
Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run
Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce
Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer
Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\StartupApproved
Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\StartupApproved\Run
Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\StartupApproved\Run32
Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\StartupApproved\StartupFolder


It's not mandatory, but why not?.



# Grand Finale

That's it!

Thank you very much for reading through all of this, I hope this guide improved your performance in games and overall in Windows.
