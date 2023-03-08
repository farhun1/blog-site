---
title: "Powershell Customization"
date: 2022-10-25
categories: [Tech]
image: images/thumbnails/powershell-thumb.jpg
url: /powershell-customization/
draft: false
---

# Powershell
What exactly is PowerShell? Powershell is a task automation solution as well as a command line shell. Similar programs include bash, zsh, and others. PowerShell, on the other hand, is now cross-platform. It is now available for download on Windows, Mac, and Linux. This increases its versatility. But one thing people are afraid of is the command line. Powershell can only be run from the command line. So why not make it more appealing to use? We are drawn to beautiful things as humans. Furthermore, rather than using a graphical user interface, powershell allows you to perform many tasks quickly. So, if we make the terminal more appealing, we will be able to encourage more people to use it. We can now start thinking about how to improve it.

## Powershell Designing
1. Install [Terminal](https://github.com/microsoft/terminal/releases)
2. Install new [powershell](https://github.com/PowerShell/PowerShell/releases)
3. Install any Nerd Fonts https://www.nerdfonts.com/
4. Install oh-my-posh https://ohmyposh.dev/docs/installation/windows or 
	`winget install oh-my-posh`
5. Create powershell $PROFILE in Documents
    - Goto Documents
    - Make a folder name `PowerShell`
    - Make a ps1 script name ```Microsoft.PowerShell_profile.ps1```
    - Open and paste  
        ```oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH\jandedobbeleer.omp.json" | Invoke-Expression```
        - To replace the default config we need to find the config folders first.
        - To find the config folder we can search up in terminal by
            **dir ~/jandedobbeleer.omp.json /s**
        - Usually the directory is 
            **C:\Users\username\AppData\Local\Programs\oh-my-posh\themes**
        - If we like to change it, it will be like
            **oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH\powerlevel10k_rainbow.omp.json" | Invoke-Expression**
        - We can also download configs from github and run them similarly

## For Terminal Icons

 If we like to have icons for folders in terminal then we need to
    - Run this command first in terminal
	 `Install-Module -Name Terminal-Icons -Repository PSGallery`
    - Then to load it everytime we need to include it in the powershell profile. So we need to edit the profile and include
	 `Import-Module -Name Terminal-Icons`

Now we need to reload or load the profile by typing `.$PROFILE`

## For history and auto completion

If we want to enable auto completion and command history with listview then following things needs to be done.
 -  `Install-Module PSReadLine -AllowPrerelease -Force`
	 type this in terminal
   - Include this lines powershell profile ```Import-Module PSReadLine Set-PSReadLineOption -PredictionSource History Set-PSReadLineOption -PredictionViewStyle ListView Set-PSReadLineOption -EditMode Windows Set-PSReadLineKeyHandler -Key Tab -Function Complete```
- Now load the profile again by typing ```.$PROFILE```
-  Good to go