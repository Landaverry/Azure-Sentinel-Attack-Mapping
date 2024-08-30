---
description: Obtain public ip of the honey pot and connect remotely via RDP session.
---

# Accessing the Virtual Machine

Go to your virtual machines and gather the public ip of the machine to test remote desktop connection.&#x20;

![](<../.gitbook/assets/image (7).png>)

Connecting using RDP

![](<../.gitbook/assets/image (8).png>)

Login Successful:

![](<../.gitbook/assets/image (9).png>)

Turn off firewall in the VM by searching wf.msc

![](<../.gitbook/assets/image (10).png>)

Turn off the firewall within the windows defender firewall properties. Do this for domain, private, and public profiles then hit apply.&#x20;

![](<../.gitbook/assets/image (11).png>)

![](<../.gitbook/assets/image (12).png>)

Now that the firewall has been shutoff, we next have to run a powershell script.&#x20;

Open and run the PowerShell ISE and copy the following code - [PowerShell Script](https://github.com/joshmadakor1/Sentinel-Lab/blob/main/Custom\_Security\_Log\_Exporter.ps1)

This script requires an API key from [https://ipgeolocation.io/] *For Security Purposes, the API key in the screenshot below has already been revoked* (https://ipgeolocation.io/)&#x20;

Once an API key has been obtained the script will continously loop searching for events of failed RDP attempts.&#x20;

Please note that the free version of the API is only limited to 1000 API requests daily.&#x20;

![](<../.gitbook/assets/image (13).png>)

The Powershell Script outputs a file to C:\ProgramData, if there is no longer file that exists within the C:\ProgramData folder it will create a default log file.&#x20;

As the script runs it generates purple output whenever a failed login event occurs. As people discover the virtual machine over the internet this will populate and more entries will appear in the log file. &#x20;

![](<../.gitbook/assets/image (14).png>)

