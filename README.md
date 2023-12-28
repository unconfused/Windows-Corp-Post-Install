# Windows-Corp-Post-Install

All the things I do to install single-user or non-administrative software as much as possible on my corporate provided laptop.

## Updates and updaters

Work with IT Services to get updater and admin-only apps running:

* Lenovo Commercial Vantage
* F5 VPN
* 

## Non-Admin runner

Save to a file "nonadmin.bat"

    cmd /min /C "set __COMPAT_LAYER=RUNASINVOKER && start "" %1"

Drag and drop programs on this to run as non-admin.

## Powershell

    Things

## Chocolatey

    https://docs.chocolatey.org/en-us/choco/setup#non-administrative-install

Create the file:  "ChocolateyInstallNonAdmin.ps1"

    # Set directory for installation - Chocolatey does not lock
    # down the directory if not the default
    $InstallDir='C:\ProgramData\chocoportable'
    $env:ChocolateyInstall="$InstallDir"
    
    # If your PowerShell Execution policy is restrictive, you may
    # not be able to get around that. Try setting your session to
    # Bypass.
    Set-ExecutionPolicy Bypass -Scope Process -Force;
    
    # All install options - offline, proxy, etc at
    # https://chocolatey.org/install
    iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

Make sure you change the $InstallDir to whatever you actually want.

In a Powershell session run:

    Set-ExecutionPolicy Bypass -Scope Process -Force;

Then run the ChocolateyInstallNonAdmin.ps1 file.

Apps that can be installed:

    choco install git.commandline -y
    choco install notepadplusplus.commandline -y

Other options:

    https://community.chocolatey.org/packages?q=id%3Aportable
