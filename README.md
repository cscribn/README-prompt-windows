# README-shells

## Windows

All commands should be executed via Windows Powershell, run as Administrator, unless otherwise specified.

### Chocolatey

Install

```pwsh
choco upgrade chocolatey -y || Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

### Curl

Install

```
choco upgrade curl -y
```

### Git

Install

```
choco upgrade git -y
```

### Fonts

Install

```pwsh
Set-Location "$Env:Windir\Fonts"

curl -Lo "Meslo LG S Regular Nerd Font Complete Windows Compatible.ttf" https://github.com/ryanoasis/nerd-fonts/raw/master/patched-fonts/Meslo/S/Regular/complete/Meslo%20LG%20S%20Regular%20Nerd%20Font%20Complete%20Windows%20Compatible.ttf

reg add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Fonts" /v "MesloLGS NF" /t REG_SZ /d "Meslo LG S Regular Nerd Font Complete Windows Compatible.ttf" /f

Set-Location -
```

### Oh-My-Posh

Install

```pwsh
choco upgrade oh-my-posh -y

Remove-Item -Recurse -Force "$Env:USERPROFILE\.config\oh-my-posh"

git clone https://github.com/cscribn/config-oh-my-posh.git  "$Env:USERPROFILE\.config\oh-my-posh"
```

### Zsh

Install

```pwsh
Remove-Item -Recurse -Force "$Env:USERPROFILE\.config\zsh"

git clone https://github.com/cscribn/config-zsh.git  "$Env:USERPROFILE\.config\zsh"

Copy-Item -Recurse -Force -Path "$Env:USERPROFILE\.config\zsh\zsh.pkg\*" -Destination "C:\Program Files\Git"

Copy-Item -Force -Path "$Env:USERPROFILE\.config\zsh\zshrc-win" -Destination "$Env:USERPROFILE\.zshrc"

Remove-Item -Recurse -Force "$Env:USERPROFILE\.zsh\zsh-autocomplete"

Remove-Item -Recurse -Force "$Env:USERPROFILE\.zsh\zsh-autosuggestions"

Remove-Item -Recurse -Force "$Env:USERPROFILE\.zsh\zsh-syntax-highlighting"
```

### Kitty

Install

```pwsh
choco upgrade kitty -y
```

Configure

1. Window -> Appearance -> Font to "MeslowLGS NF"
1. Font Quality = Anti-Aliased

### PowerShell Core

Install

```pwsh
choco upgrade powershell-core -y

Install-Module -Name Terminal-Icons -Repository PSGallery

Install-Module PSReadLine -AllowPrerelease -Force
```

### ConEmu (Windows < 10)

Install

```pwsh
choco upgrade conemu -y
```

### Microsoft Windows Terminal (Windows >= 10)

Install

```pwsh
choco upgrade microsoft-windows-terminal -y

$LocalStateDir = Get-ChildItem -Path "$Env:LOCALAPPDATA\Packages\Microsoft.WindowsTerminal_*\LocalState"

curl -Lo "$LocalStateDir\settings.json" https://raw.githubusercontent.com/cscribn/config-misc/main/microsoft-windows-terminal/LocalState/settings.json
```

### Vim

Install

```pwsh
choco upgrade vim -y
```

### Visual Studio Code

Install

```pwsh
choco upgrade vscode -y
```
