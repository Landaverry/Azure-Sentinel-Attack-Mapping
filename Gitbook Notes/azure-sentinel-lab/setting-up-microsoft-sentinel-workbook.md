---
description: Mapping the custom query to Microsoft Sentinel
---

# Setting Up Microsoft Sentinel Workbook

Go to Microsoft Sentinel > Workbooks and create a new workbook

Add a new query and run:

![](<../.gitbook/assets/image (18).png>)

Under Visualization select 'Map"

![](<../.gitbook/assets/image (19).png>)

KQL Script:

```custom.2
Failed_RDP_with_GEO_CL_CL
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

Adjust Map settings as needed or you can base location information by Country instead of by longitude and Latitude.

![](<../.gitbook/assets/image (20).png>)

Wait Several Hours to see how many other attackers attempt to login onto the honeypot:\
![](<../.gitbook/assets/image (21).png>)
