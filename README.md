# SIEM Network Forensics and Incident Response Home Lab

## 📝 Objective

To build a defensive lab to conduct a SIEM (Security Information & Event Management), network forensics and malware analysis environment.

___

## 🔨 Tools Used

- VMware Workstation Pro 17
- Ubuntu
- REMNux
- Windows 11
- Cloudflare (Flare VM)
- Splunk

___

## Ubuntu (Splunk)

I started installing Ubuntu and named it after the latest version along with it is a clean slate. This will be the core of the isolation and I will install on top of the Ubuntu image an instance of Splunk for log arregation and analysis.

Before getting started, I update and upgrade the Ubuntu machine: 

<pre>sudo apt update && sudo apt upgrade</pre>

## Splunk

I went to the official Splunk website and selected the Free Trials & Downloads page. As I am there, I went ahead and selected the Splunk Enterprise trial. I filled out the required information and moved the splunk compressed debian package to /opt directory.

<pre>mv splunk (version-os-architecture-package) /opt/</pre>

I selected the splunk compressed debian package on the /opt directory and initiate the installation.

<img width="2172" height="1372" alt="splunk" src="https://github.com/user-attachments/assets/aba7e5a3-040c-42af-9b34-078f66ab7eb9" />

To start Splunk,

<pre>sudo /opt/splunk/bin/splunk start --accept-license</pre>


As I started this, I went to my localhost of Splunk Enterprise:

<img width="1487" height="322" alt="splunk enterprise" src="https://github.com/user-attachments/assets/fd309976-f047-4ea8-a0e8-89ebc3969ec3" />

From there, I will be heading to the GitHub repository to get sample data from Splunk BOSS of the SOC version 3. Once I am there, I've downloaded their data set and started to decompress the file:

```tar -xvzf <botsv3_dataset.tgz>```

I am moving the data set to a different path:

```mv botsv3_data_set /opt/splunk/etc/apps```

```sudo !!```

Now, I just do the same proceed to start Splunk and logged in. I go to Settings > Server Controls > Restart Splunk.

Once the action is done, now it's time for the data set to pop up. Go ahead and go to App > Manage Apps > Enable the data set.

I went to the Apps > Search & Reporting and started to do my Splunk Searches. I followed the GitHub Repository (botsv3) which linked below on the References section.

## REMNux

I went ahead and turned on my cloned Ubuntu machine. Now, I am going to pull REMNux from their site to start up the installation.

```wget https://REMnux.org/remnux-cli```

Once that is done, I started to move it and to modify permissions:

```mv remnux-cli remnux```

```sudo chmod +x remnux```

```sudo mv remnux /usr/local/bin```

Installing curl to gather dependencies:

```sudo apt install -y gnupg curl```

Downloading a Virtual Appliance File using the General OVA from the REMNux official site:

<img width="3086" height="1767" alt="REMNux" src="https://github.com/user-attachments/assets/0b1e6444-b3d2-47bd-b359-66bd98720d2b" />

```powershell
Get-FileHash -Algorithm SHA256 .\remnux-v7-focal.ova
```

Once I am at my REMNux, I will upgrade it:

```remnux upgrade```

As the upgrade has finished, I am going to take a snapshot of the vm resembling a clean slate.

<img width="3477" height="1696" alt="REMNux2" src="https://github.com/user-attachments/assets/564f5ec2-e94a-4b42-9d1f-5b1acd32520b" />


## Windows 11 (Flare VM)

I will be setting up a Windows 11 VM to install Flare VM. Set the Network Adapter to VMNet0 so, we can have an isolated environment and being able to have a sandbox type feeling.

Press Shift+fn+10 to bypass Windows connection to the network and enter the following command:

```OOBE\BYPASSNRO```

<img width="956" height="515" alt="connection2" src="https://github.com/user-attachments/assets/9f426508-8a20-4c6b-a791-53f789f13a09" />


As I bypassed of not setting up the network, I restarted my Windows 11 VM and followed the procedures to install Flare VM:

Windows Defender needs to be removed:

So, I went to a GitHub repository and downloaded the Windows Defender Remover on the Releases page. I ran the executable file to remove Defender completely.

Once I have done that, I created a snapshot as a Pre-ToolKit.

<img width="1490" height="1426" alt="Pre-ToolKit" src="https://github.com/user-attachments/assets/0661ae19-10b8-4627-9c2b-87b9073f5d36" />

I went ahead and opened Windows PowerShell as an Administrator.

I ran the following commands:

```powershell
Get-ExecutionPolicy
```

```powershell
Set-ExecutionPolicy Unrestricted -Force
```

FLARE-VM Installation

```powershell
(New-Objectnet.webclient).DownloadFile('https://raw.githubusercontent.com/mandiant/flare-vm/main/install.ps1',"$([Environment]::GetFolderPath("Desktop"))\install.ps1")
```

```powershell
cd .\Desktop\
```

```powershell
.\install.ps1
```

Once FlareVM has installed, I am able to see this wonderful background on my Windows 11 VM:

<img width="1580" height="1393" alt="Flare VM" src="https://github.com/user-attachments/assets/cde8a360-9fd1-4942-9c0c-42e499bbbb02" />


## Future Improvements

I plan to utilize this lab to conduct more SIEM, network forensics, and malware analysis activities.

___

## References

[Hack The Box - Building a defense lab](https://youtu.be/eWQ99r4zZ-8?si=9BkSeDD1CRhMuIDt)

[GitHub - Boss of the SOC (BOTS) Dataset Version 3](https://github.com/splunk/botsv3)

[GitHub - Windows Defender Remover](https://github.com/ionuttbara/windows-defender-remover)

[Splunk Download](https://www.splunk.com/en_us/download.html)

[Windows 11 ISO Download](https://www.microsoft.com/en-us/software-download/windows11)

[REMNux Download](https://docs.remnux.org/install-distro/get-virtual-appliance)
