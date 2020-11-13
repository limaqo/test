---
title: "Proton via Steam"
permalink: /proton-via-steam/
author_profile: false
sidebar:
  nav: "docs"
---

Proton via Steam sample text.

y### Steam installer
* install "Steam installer" via Ubuntu Software
* run Steam and wait for installation
* Settings → "In-Game" tab
  * In-game FPS counter: Top-right
* Settings → "Steam Play" tab
  * Enable Steam Play for all other titles (y)
  * Run other titles with: Proton 5.0-9 ("Steam Linux Runtime - Soldier" did not work back then)
* Divinity Original Sin 2
  * https://www.reddit.com/r/DivinityOriginalSin/comments/alrg6u/divinity_original_sin_2_de_on_linux_with/
    * Browse local files
    * right click in Dolphin crashes
    * F4 opens terminal
    * `mv bin bin~`
    * `ln -s DefEd/bin bin`
    * `cd bin`
    * `mv SupportTool.exe SupportTool.exe~`
    * `ln -s EoCApp.exe SupportTool.exe`
  * launch the game
  
* Saves have no Screenshot
* Microsoft .NET framework is always tried to be installed at startup
* cast cursor lags behind when quick mouse movements