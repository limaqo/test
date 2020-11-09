---
title: "Kubuntu setup"
permalink: /kubuntu-setup/
author_profile: false
sidebar:
  nav: "docs"
toc: true
---

# Generic system update
There are two interchangeable ways to perform system updates in Kubuntu: either via [**_Discover_**](https://userbase.kde.org/Discover) or via [**_Konsole_**](https://userbase.kde.org/Konsole) (hotkey: `Ctrl+Alt+T`):
``` bash
sudo apt update
sudo apt upgrade
```

# Adjust system clock for dual boot

If you are dual booting [Ubuntu flavours](https://ubuntu.com/download/flavours) (e.g. Kubuntu) and Windows, you will notice the clock is off whenever you are switching the OS. The reason for this is that Kubuntu is maintaining the hardware clock ([RTC](https://en.wikipedia.org/wiki/Real-time_clock)) in universal time ([UTC](https://en.wikipedia.org/wiki/Coordinated_Universal_Time)) while Windows is maintaining it in [local time](https://en.wikipedia.org/wiki/Time_zone).

The preferred solution is to set Kubuntu to maintain the RTC in local time. Setting Windows to use UTC via registry settings can cause problems with applications which wrongly assume the RTC is still maintained in local time. [[How-To Geek](https://www.howtogeek.com/323390/how-to-fix-windows-and-linux-showing-different-times-when-dual-booting/)]

**solution**:

``` bash
timedatectl set-local-rtc 1 --adjust-system-clock
timedatectl # check output if change was successful
```

# Update GPU driver (Nvidia) and adapt refresh rate
* open [**_System Settings_**](https://userbase.kde.org/System_Settings)
* **_Hardware_** section → **_Driver Manager_** tab (requires password, opens **_Software Sources_**)
  * **_Additional Drivers_** tab (preselected) → activate newest **_NVIDIA driver metapackage_**
    * apply changes
    * reboot
    * check output of `nvidia-smi`
* **_Hardware_** section → **_Display and Monitor_** tab
  * change Display Configuration to match physical display setup
  * set Primary Display
  * adapt Refresh Rates

# Panels

If you have multiple monitors, you might want to have multiple taskbars. In [KDE Plasma](https://en.wikipedia.org/wiki/KDE#Plasma_Workspaces) taskbars are realized via [panels](https://userbase.kde.org/Plasma/Panels) which contain any number of widgets.

The **_Default Panel_** and **_Kubuntu Default Panel_** contain the following widgets in this order:

* [**_Application Launcher_**](https://userbase.kde.org/Plasma/Kickoff): The KDE equivalent of [Windows 7 start menu](https://en.wikipedia.org/wiki/Start_menu) enables you to launch applications amongst others.  
Alternative widgets are **_Application Dashboard_** (fullscreen launcher) and **_Application Menu_** (cascading popups launcher).
* [**_Pager_**](https://userbase.kde.org/Plasma/Pager): Switch between [virtual desktops](https://en.wikipedia.org/wiki/Virtual_desktop).  
Alternative widget is **_Activity Pager_** if you prefer to work with activities instead of virtual desktops. While virtual desktops are each identical, activities can be configured individually.
* [**_Task Manager_**](https://userbase.kde.org/Plasma/Tasks): Not to be confused with Windows task manager, KDE's task manager is just a list of open windows.
* [**_System Tray_**](https://userbase.kde.org/Plasma/SystemTray): Displays system information and notifications, allows you to interact with connected devices and much more depending on widget configuration.
* [**_Digital Clock_**](https://userbase.kde.org/Plasma/Clocks): Displays the time and date in the format of your choice.
* **_Show Desktop_** (Default Panel) or **_Minimize all Windows_** (Kubuntu Default Panel): The name says it all but the default hotkey `Meta+D` does the same, so feel free to remove either widget.

## Configure panels
* right click on any already existing panel → **_Edit Panel..._** to enter panel edit mode
* **_Add Widgets..._** or hover over the panel and **_Remove_** widgets as you like
  * suggestion for primary screen (central):
    * start with the existing panel
    * Application Launcher → keep
    * Pager → remove
    * Task Manager → keep
    * System Tray → keep
    * Digital Clock → keep
    * Show Desktop → remove

## Add or remove panels
* right click on an empty spot on the desktop or on any already existing panel → **_Add Panel_**
  * while in panel edit mode: drag the panel by the **_Screen Edge_** handle to the position of your choice
* while in panel edit mode: right click on the panel → **_Remove Panel_**
  * suggestion for secondary screens (left or right):
    * start with an empty panel
    * Task Manager → add

## Configure widgets
* while in panel edit mode: hover over the panel and **_Configure..._** widgets as you like
* each widget is an independent instance and thus must be configured independently from each other
  * suggested configuration
    * **_Task Manager_** widgets → **_Behavior_** tab → Show only tasks: From current screen
    * **_Digital Clock_** widgets → **_Appearance_** tab
      * Show date (enabled)
      * Show seconds (enabled)
      * Date format: Custom "dd.MM.yyyy"
      * **_Calendar_** tab → Show week numbers (enabled)

# Choosing system themes

To achive a uniform and pleasing look of applications, this paragraph is about choosing system themes. Windows and MacOS each have one uniform look by the fact that there is a company behind it enforcing it. Linux is far more fragmented which is both good and bad.

Kubuntu's desktop environment [KDE Plasma](https://en.wikipedia.org/wiki/KDE#Plasma_Workspaces) is built around the widget toolkit [Qt](https://en.wikipedia.org/wiki/Qt_(software)). Its default theme "Breeze" is responsible for GUI elements' look. The arrangement of GUI elements often follows the widget toolkit's convention which is one reason why programs using Qt might feel a little different than those using GTK. [GTK](https://en.wikipedia.org/wiki/GTK) is the other prevalent widget toolkit under Linux which was originally written for the raster graphics editor [GIMP](https://en.wikipedia.org/wiki/GIMP).

Luckily the "Breeze" theme is preinstalled for both Qt and GTK on Kubuntu. If you are interested in other themes, feel free to choose from the plethora of other themes available for download through the System Settings.

To achieve a uniform look, you need three themes for Qt, GTK2 and GTK3. Although in practice two themes for Qt and GTK3 might be enough as I didn't find any applications still using the outdated GTK2 widget framework yet. Adjusting the look of Qt is prominently located in the System Settings while the GTK settings are a little more hidden.

acquainted applications using GTK: Firefox, Thunderbird, GIMP and a lots of other applications starting with "G" which are close or part of the [GNOME](https://en.wikipedia.org/wiki/GNOME) desktop environment

acquainted applications using Qt: OBS, OpenShot, Teamviewer, VLC, Wireshark and lots of applications starting either with "K" or "Q" which are close or part of the KDE Plasma desktop environment.

* open [**_System Settings_**](https://userbase.kde.org/System_Settings)
* you probably __DO NOT__ want to change the **_Global Theme_** as those presets can change settings beyond the **_Appearance_** section, e.g. the task switcher
  * if the **_Global Theme_** was changed, the default **_Application Launcher_** (called "Start Menu" on Windows) icon can be found at `/usr/share/plasma/desktoptheme/kubuntu/icons/start.svgz`
    * right click on **_Panel_** (called "Task Bar" on Windows) containing the **_Application Launcher_** to edit
    * hover over the **_Application Launcher_** icon to configure
    * **_General_** tab → select desired icon
* **_Appearance_** section
  * **_Application Style_** tab → **_Application Style_** tab (preselected) → **_Configure GNOME/GTK Application Style_**
    * GTK2 theme: Breeze-Dark
    * GTK3 theme: Breeze-Dark
  * **_Colors_** tab
    * Colors: Breeze Dark
  * **_Icons_** tab
    * Icons: Breeze Dark

# Window manipulation hotkeys
Hotkeys are called "Shortcuts" on Kubuntu.
* open [**_System Settings_**](https://userbase.kde.org/System_Settings)
* **_Workspace_** section → **_Shortcuts_** tab → **_Global Shortcuts_** tab (preselected) → **_System Services_** section → **_KWin_**

| Function                              | Primary hotkey               | Secondary hotkey             |
|---------------------------------------|------------------------------|------------------------------|
| Maximize Window                       | Meta+Up   (Reassign)         | Global Alternate: Meta+Num+5 |
| Minimize Window                       | Meta+Down (Reassign)         | Global Alternate: Meta+Num+0 |
| Quick Tile Window to the Bottom       | --                           |                              |
| Quick Tile Window to the Bottom Left  | Meta+Num+1                   |                              |
| Quick Tile Window to the Bottom Right | Meta+Num+3                   |                              |
| Quick Tile Window to the Left         | Global Alternate: Meta+Num+4 |                              |
| Quick Tile Window to the Right        | Global Alternate: Meta+Num+6 |                              |
| Quick Tile Window to the Top          | --                           |                              |
| Quick Tile Window to the Top Left     | Meta+Num+7                   |                              |
| Quick Tile Window to the Top Right    | Meta+Num+9                   |                              |
 
ToDo: "(overwrite alternate New Tab shortcut)" - what did I mean by this?
    
# Screenshot hotkey
If you want a Windows-like screenshot hotkey, this is how you can do it:
* open [**_System Settings_**](https://userbase.kde.org/System_Settings)
* **_Workspace_** section → **_Shortcuts_** tab → **_Global Shortcuts_** tab → **_Application Launchers_** tab
  * **_Spectacle_** tab → Capture Rectangular Region: Meta+Shift+S

# Change task switcher (Alt+Tab)
* open [**_System Settings_**](https://userbase.kde.org/System_Settings)
* **_Workspace_** section → **_Window Management_** tab → **_Task Switcher_** tab → **_Main_** tab (preselected)
  * change **_Breeze_** to **_Grid_** (closest to Windows default)

# Disable animations
* open [**_System Settings_**](https://userbase.kde.org/System_Settings)
* **_Workspace_** section → **_Workspace Behavior_** tab → **_General Behavior_** tab (preselected)
  * Animation speed: Instant