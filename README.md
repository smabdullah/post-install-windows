# post-install-windows
Automate and simplify post-installation tasks on Windows using **Winget** and **Chocolatey**.

![visual](/DALL·E%202024-12-17%2012.05.53%20-%20A%20clean%20and%20modern%20workflow%20diagram%20for%20automating%20post-installation%20tasks%20on%20Windows.%20The%20design%20should%20feature%20a%20professional%20layout%20with%20soft%20blue%20.png)

Setting up a freshly installed Windows 10 or 11 computer can be tedious and time-consuming, especially when you have to manually install each application you need. This tutorial will guide you through automating most of the package installation process, saving you time and ensuring you have a reusable setup for future reinstalls.

We will use [Winget](https://learn.microsoft.com/en-us/windows/package-manager/winget/), a built-in Windows package manager, and [Chocolatey](https://chocolatey.org/), a popular package management tool, to streamline the process.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Step-by-Step Guide](#step-by-step-guide)
- [Package Categories](#package-categories)
- [Troubleshooting](#troubleshooting)
- [Maintenance](#maintenance)

## Prerequisites
Before starting, ensure you have:
- Windows 10 (1809 or later) or Windows 11
- Administrator access
- Active internet connection

## Step-by-Step Guide

### Step 1: Install Chocolatey Using Winget
1. Open a terminal as an administrator.
2. Run the following command to install Chocolatey:
```bash
winget install Chocolatey.Chocolatey

```
### Step 2: Close the Terminal.
After the installation completes, close the terminal.

### Step 3: Create a Configuration File
1. Create a configuration file (e.g., packages.config) to list all the packages you want to install. There is an example configuration file included in this repository.
2. Visit the [Chocolatey package repository](https://community.chocolatey.org/packages) to find the package names for your desired applications (e.g., googlechrome for Chrome)
3. Add these package names to your configuration file.

### Step 4: Install Packages from the Configuration File
1. Open a terminal as an administrator.
2. Run the following command to install all the packages:
```bash
choco install packages.config --yes
```
Replace `packages.config` with the name of your configuration file.

Chocolatey will begin installing the listed packages. This process is fully automated and requires no input, allowing you to focus on other tasks while it runs.

### Step 5: Review the Installation Log
Once the process completes, Chocolatey will display a summary of successes and failures. If a package fails to install, you can try installing it manually. For example, I encountered as issue with `googledrive` and had to install it separately.

### Step 6: Restart your Computer
After the installations are complete, restart your computer to ensure everything is set up correctly. Enjoy your newly configured system!

## Package Categories
The example `packages.config` includes:

### Development Tools
- Git: Version control
- VS Code: Code editor
- Notepad++: Text editor

### Web Browsers
- Google Chrome
- Brave: Privacy-focused browser

### System Utilities
- PowerToys: Windows power-user tools
- Everything: Fast file search
- 7zip: File compression
- HWiNFO: System information

### AI & Productivity
- Ollama: Local AI models
- PDFGear: PDF viewer and editor

## Troubleshooting

### Common Issues
1. **Package Installation Failures**
   - Try running the command again
   - Check your internet connection
   - Run `choco install [package-name] -v` for verbose output

2. **Permission Issues**
   - Ensure you are running as administrator

3. **Chocolatey Installation Issues**
   - Try installing manually from chocolatey.org
   - Check system requirements

## Maintenance

### Updating Packages
To update all installed packages:
```bash
choco upgrade all --yes
```

To update specific packages:
```bash 
choco upgrade [package-name]
```

### Uninstalling Packages
To remove a package:
```bash
choco uninstall [package-name]
```