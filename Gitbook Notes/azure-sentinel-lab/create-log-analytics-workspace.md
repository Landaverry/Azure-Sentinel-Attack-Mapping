---
description: >-
  Creating the Log Analytics Workspace that will connect to Microsoft Sentinel
  to display the geographical data on a map.
---

# Create Log Analytics Workspace

A Log Anlaytics Workspace needs to be created in the newly created resource group. This workspace will be used to ingest logs from the virtual honey pot. The purpose of this workspace will be to store and gather logs from the windows event manager from within the honey pot, and create a custom log containing geographical information to identify the location and origin of attackers.&#x20;



![](<../.gitbook/assets/image (3).png>)

Next go to Microsoft Defender for Cloud > Enviornment Settings and turn on defender to enable log gathering. Click Save.&#x20;

![](<../.gitbook/assets/image (4).png>)

Next go back to the Log Analytics Worspace and add the Honey Pot.&#x20;

![](<../.gitbook/assets/image (5).png>)
