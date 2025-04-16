# PowerShell script to install multiple programs using Chocolatey
When setting up a new computer, it can be annoying to install all the various programs that you use regularly. As I was working on a new computer, I thought to myself, "Why do this by hand when I can automate it?" Hence, I came up with the following script that allows me to install a list of programs. You can remove or delete programs from the list as needed. If you want to add a new program, just make sure that the program name matches the Chocolatey package name (the Windows version of a package manager). You can search for those programs here: Chocolatey Packages.

# Function to install Chocolatey if not already installed
 
 ``` 
 
  function Install-Chocolatey {
      if (-Not (Get-Command choco -ErrorAction SilentlyContinue)) {
          Write-Host "Installing Chocolatey..."
          Set-ExecutionPolicy Bypass -Scope Process -Force
          [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.SecurityProtocolType]::Tls12
          Invoke-Expression ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
      } else {
          Write-Host "Chocolatey is already installed."
      }
  }
  
```

# Install Chocolatey
```
Install-Chocolatey
```

# List of programs to install
```
$programs = @(
    "notepadplusplus.install",
    "postman",
    "soapui",
    "wsl2",
    "cygwin",
    "7zip.install",
    "filezilla",
    "winscp",
    "teamviewer",
    "vlc",
    "putty",
    "wireshark",
    "virtualbox"
    "steam"
    "podman-desktop"
    "goggalaxy"
    "rustdesk"
    "brave"
    "python3"
    "vscodium"
    "awscli"
    "curl"
    "windirstat"
    "firefox"
    "wireguard"
    "yt-dlp"
    "powertoys"
    "terraform"
    "minikube"
)
```

# Function to check if a program is installed
```
function Is-ProgramInstalled {
    param (
        [string]$program
    )
    # Check if the program is installed using Chocolatey
    $installedPackages = choco list --local-only | Select-String $program
    return $installedPackages -eq $null
}
```

# Install each program if not already installed

```
foreach ($program in $programs) {
    if (Is-ProgramInstalled $program) {
        Write-Host "Installing $program..."
        choco install $program -y
    } else {
        Write-Host "$program is already installed. Skipping..."
    }
}

Write-Host "All specified programs have been processed."
```

# Complete Script
```
# PowerShell script to install multiple programs using Chocolatey

# Function to install Chocolatey if not already installed
function Install-Chocolatey {
    if (-Not (Get-Command choco -ErrorAction SilentlyContinue)) {
        Write-Host "Installing Chocolatey..."
        Set-ExecutionPolicy Bypass -Scope Process -Force
        [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.SecurityProtocolType]::Tls12
        Invoke-Expression ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
    } else {
        Write-Host "Chocolatey is already installed."
    }
}

# Install Chocolatey
Install-Chocolatey

# List of programs to install
$programs = @(
    "notepadplusplus.install",
    "postman",
    "soapui",
    "wsl2",
    "cygwin",
    "7zip.install",
    "filezilla",
    "winscp",
    "teamviewer",
    "vlc",
    "putty",
    "wireshark",
    "virtualbox"
    "steam"
    "podman-desktop"
    "goggalaxy"
    "rustdesk"
    "brave"
    "python3"
    "vscodium"
    "awscli"
    "curl"
    "windirstat"
    "firefox"
    "wireguard"
    "yt-dlp"
    "powertoys"
    "terraform"
    "minikube"
)

# Function to check if a program is installed
function Is-ProgramInstalled {
    param (
        [string]$program
    )
    # Check if the program is installed using Chocolatey
    $installedPackages = choco list --local-only | Select-String $program
    return $installedPackages -eq $null
}

# Install each program if not already installed
foreach ($program in $programs) {
    if (Is-ProgramInstalled $program) {
        Write-Host "Installing $program..."
        choco install $program -y
    } else {
        Write-Host "$program is already installed. Skipping..."
    }
}

Write-Host "All specified programs have been processed."
```
