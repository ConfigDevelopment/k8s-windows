# k8s

1️⃣ Bật WSL và VM Platform
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

# Bật Virtual Machine Platform (cần cho WSL2)
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

# Khởi động lại server
Restart-Computer

2️⃣ Đặt WSL2 làm mặc định

Sau khi khởi động lại:

wsl --set-default-version 2
https://aka.ms/wslubuntu2204

3️⃣ Tải Ubuntu 22.04 cho WSL

Trên máy Windows Server (không có Microsoft Store), bạn tải trực tiếp file Appx:

[👉 Ubuntu 22.04 Appx](https://aka.ms/wslubuntu2204)

Ví dụ tải về thành Ubuntu2204-221101.appxbundle.
# Đổi tên file appx thành zip
cd "D:\Program Files\WSL"
Rename-Item "Ubuntu2204-221101.appxbundle" "Ubuntu2204.zip"

# Giải nén vào thư mục đã tạo sẵn
Expand-Archive "Ubuntu2204.zip" "D:\Program Files\WSL\Ubuntu2204"

cd "D:\Program Files\WSL\Ubuntu2204"

# Đổi tên appx thành zip
Rename-Item "Ubuntu_2204.1.7.0_x64.appx" "Ubuntu_2204.1.7.0_x64.zip"

# Giải nén zip ra thư mục Extracted
Expand-Archive "Ubuntu_2204.1.7.0_x64.zip" -DestinationPath "D:\Program Files\WSL\Ubuntu2204\Extracted"

Cài ubuntu
mkdir "D:\WSL\Source"
Copy-Item "D:\Program Files\WSL\Ubuntu2204\Extracted\install.tar.gz" "D:\WSL\Source\install.tar.gz"
wsl --import Ubuntu-22.04 "D:\WSL\Ubuntu2204" "D:\WSL\Source\install.tar.gz"

PS C:\WINDOWS\system32> systeminfo | find "Virtualization"
FIND: Parameter format not correct
PS C:\WINDOWS\system32> systeminfo | Select-String "Virtualization"

Virtualization-based security: Status: Running
                                     Base Virtualization Support

check BIOS

dism.exe /online /enable-feature /featurename:Microsoft-Hyper-V /all /norestart
dism.exe /online /enable-feature /featurename:Microsoft-Hyper-V-Management-Clients /all /norestart
dism.exe /online /enable-feature /featurename:Microsoft-Hyper-V-Management-PowerShell /all /norestart
dism.exe /online /enable-feature /featurename:HypervisorPlatform /all /norestart
