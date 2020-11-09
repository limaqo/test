---
title: "Applications"
permalink: /applications/
author_profile: false
sidebar:
  nav: "docs"
toc: true
---

y### Spectacle (Screenshot Utility)
* "Capture Mode" section
  * Area: Rectangular Region
* Configure → "General" tab 
  * Press screenshot key to, Return focus to Spectacle (y)
  * After taking a screenshot, Copy image to clipboard (y)
  * After taking a screenshot, Autosave the image to the default location (y)
  * General, Show magnifier (y)

y### Grub
* install "Grub Customizer" via "Discover"
* rename entries (via double click)
* order entries as desired
* save

y### Firefox
* Preferences → "General" tab → "Startup" section
  * Restore previous session (y)
  * Always check if Firefox is your default browser (y)
* about:config
  * smooth scrolling:
    * mousewheel.min_line_scroll_amount: 50
    * general.smoothScroll.mouseWheel.durationMaxMS: 500
    * general.smoothScroll.mouseWheel.durationMinMS: 300
  * tearing fix:
    * layers.acceleration.force-enabled: true
* Customize (right under Preferences)
  * Toolbars (at the bottom left of the screen) → Bookmarks Toolbar (y)
* Add-ons
  * install uBlock Origin (Allow in private?)
* visit www.startpage.com
  * install Startpage add-on (Allow in private?)
  * change Startpage.com to default search engine
* visit startpage.com → Settings
* "Results Appearance" section
  * Open search result in a new window (n)
* "Privacy and Safety" section
  * Only connect to servers that are: EU servers
  
y### Kate (Text Editor)
* if launching Kate from terminal gives error:
```
Hspell: can't open /usr/share/hspell/hebrew.wgz.sizes.
sonnet.plugins.hspell: HSpellDict::HSpellDict: Init failed
```
then 
`sudo apt install hspell`
* "Editor Component" → "Appearance" tab
  * Whitespaces: All
* "Editor Component" → "Editing" → "General" tab
  * Show static word wrap marker (y)
  * Wrap words at: 120

y### Dolphin (File Explorer)
Hotkeys:
Ctrl+L: toggle location bar
F4: toggle terminal
Ctrl+H: toggle hidden files
* Configure Keyboard Shortcuts
  * Create Folder: Ctrl+Shift+N (overwrite alternate New Tab shortcut)
  * Activate Next Tab: Ctrl+Right
  * Activate Previous Tab: Ctrl+Left
* Show Previews (n)
* top left of window → Details view mode (y)
* bottom center of window (Slider) → Size: 22 pixels
* Configure Dolphin → "Behavior" tab → Show selection marker (n)

y### Konsole (Terminal)
* Settings → Configure Keyboard Shortcuts
  * New Tab:       Ctrl+T
  * Close Session: Ctrl+W
  * Previous Tab:  Ctrl+Left
  * Next Tab:      Ctrl+Right
* Settings → Configure Konsole → "Tab Bar" tab
  * Position: Above terminal area
* `kate ~/.inputrc` (probably empty document)
  * add 1st line: `"\e[A":history-search-backward`
  * add 2nd line: `"\e[B":history-search-forward`
* restart console to activate changes
* what colors are what: `find . -maxdepth 1 -exec stat --printf='%F\t%n\n' '{}' \; | sort`

### Meld
* install "Meld" via Ubuntu Software

### QDirStat
* sudo apt install qdirstat

### Timeshift
* source code with README.md: https://github.com/teejee2008/timeshift
* install Timeshift via Ubuntu Software
* open Timeshift and complete the setup:
  * RSYNC → partition → snapshot levels → home folders(?)
* create a snapshot

* 139,7 available -> xxx ?

### KolourPaint
install KolourPaint from Discover