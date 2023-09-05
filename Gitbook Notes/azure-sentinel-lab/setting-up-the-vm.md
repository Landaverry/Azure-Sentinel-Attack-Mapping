---
description: Setting up VM - Honey Pot for Lab.
---

# Setting Up the VM

Create an account in Azure and create a virutal machine and resource group.&#x20;

AVOID common usernames and passwords.&#x20;



![](<../.gitbook/assets/image (2).png>)

Once you get to the networking tab, select 'Advanced' NIC network Security group and create a new security group. This will allow us to modify the Azure firewalls to establish an ALLOW all rule to help log attacker traffic.&#x20;

Network Security groups act like firewalls in Azure. We are creating this inbound rule INTENTIONALLy to make the VM easily discoverable for potential attackers.&#x20;

![](<../.gitbook/assets/image (1) (1).png>)

Inbound Rule:&#x20;

![](<../.gitbook/assets/image (2) (1).png>)

Proceed to review the settings and create the VM.&#x20;
