---
description: >-
  Create custom log in Azure log analytics workspace to digest the powershell
  script output
---

# Creating Custom Log in Log Analytics Workspace

On local machine create a sample\_log.txt file that contains the contents of the failed.rdp log file. This will be used later to train the log anayltics workspace.&#x20;

To create the custom log within the Azure portal go to Log Analytics Workspace > Tables

Create a new table > MMA Based > select sample log stored on local machine.&#x20;

![](<../.gitbook/assets/image (15).png>)

Hit next. Under the collection path, give the location of the custom log that is output from the powershell script on the honey pot: C:\ProgramData\failed\_rdp.log

![](<../.gitbook/assets/image (16).png>)

Name the custom log and create.&#x20;

![](<../.gitbook/assets/image (17).png>)

Please not that it may take some time for the log analytics workspace to sync up with the honey pot before it displays the log entries.&#x20;

using the following KQL query to extract certain fields from the raw data and exclude the sample data

```
[enter the name of your custom script here]
| extend username = extract(@"username:([^,]+)", 1, RawData),
         timestamp = extract(@"timestamp:([^,]+)", 1, RawData),
         latitude = extract(@"latitude:([^,]+)", 1, RawData),
         longitude = extract(@"longitude:([^,]+)", 1, RawData),
         sourcehost = extract(@"sourcehost:([^,]+)", 1, RawData),
         state = extract(@"state:([^,]+)", 1, RawData),
         label = extract(@"label:([^,]+)", 1, RawData),
         destination = extract(@"destinationhost:([^,]+)", 1, RawData),
         country = extract(@"country:([^,]+)", 1, RawData)
| where destination != "samplehost"
| where sourcehost != ""
| summarize event_count=count() by latitude, longitude, sourcehost, label,destination, country

```

If you run this query and you can see extracted logs then you can proceed with setting up a workbook in Microsoft Sentinel.&#x20;
