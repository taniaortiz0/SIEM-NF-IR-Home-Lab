# SIEM Network Forensics and Incident Response Home Lab (work-in-progress)

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

## Ubuntu (Splunk + REMNux)

I started installing Ubuntu and named it after the latest version along with it is a clean slate. This will be the core of the isolation and I will install on top of the Ubuntu image an instance of Splunk for log arregation and analysis.

Similarily to this process, I am going to utilize another Ubuntu VM (full clone) to setup a Reverse Engineering Malware Analysis image using REMNux.

Before getting started, update and upgrade the Ubuntu machine: 

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

From there, I will be heading to the GitHub repository to get sample data from Splunk BOSS of the SOC version 3.



## REMNux


## Windows 11 (Cloudflare Flare VM)

I will be setting up a Windows 11 VM to create a Forensics Reverse Engineering toolkit such as Flare VM.

____

___

## References

[Hack The Box - Building a defense lab](https://youtu.be/eWQ99r4zZ-8?si=9BkSeDD1CRhMuIDt)

[GitHub - Boss of the SOC (BOTS) Dataset Version 3](https://github.com/splunk/botsv3)

[Splunk Download](https://www.splunk.com/en_us/download.html)

[Windows 11 ISO Download](https://www.microsoft.com/en-us/software-download/windows11)

[REMNux Download](https://docs.remnux.org/install-distro/get-virtual-appliance)
