# Kali Security Tools

The second part of the lab focused on choosing a Kali Linux tool for different security scenarios and explaining why it would be a good choice. I researched the tools below, but I did not run them as part of this lab.

## Tools I Researched

| Scenario | Tool | Why I Chose It |
| --- | --- | --- |
| Create a copy of a drive before examining it | Guymager | It can create a forensic image without requiring analysis on the original drive |
| Find a web server using TCP port 443 | Nmap | It can scan an authorized network to find hosts with a specific port open |
| Look for traffic using TCP port 443 without scanning | Wireshark | It can capture and filter traffic that is visible from the system running it |
| Monitor nearby Bluetooth devices | BlueHydra | It can discover and track Classic Bluetooth and Bluetooth Low Energy devices |
| Review the code of a compiled Android application | JADX | It can decompile APK and DEX files into readable Java-like code |

## Guymager

For a scenario involving a hard drive that might contain evidence, I chose Guymager. It can create a bit-for-bit image of a storage device so the copy can be examined instead of working directly with the original drive.

The main idea I learned from this scenario was to preserve the original evidence first. Creating an image does not decrypt an encrypted drive, but it gives the investigator a copy to work with and helps protect the original device from accidental changes.

## Nmap

I chose Nmap for finding a host with TCP port 443 open on an authorized network. Nmap is an active scanning tool, which means it sends traffic to hosts and records their responses.

An example using an address range reserved for documentation is:

~~~bash
nmap -p 443 192.0.2.0/24
~~~

The command checks the /24 network for hosts listening on port 443. An open port shows that a service is accepting connections, but it does not prove that the service is vulnerable.

## Wireshark

For the passive version of the network scenario, I chose Wireshark. Instead of sending scan traffic, Wireshark captures traffic that is already visible from the system's location on the network.

This display filter can narrow the captured traffic to TCP port 443:

~~~text
tcp.port == 443
~~~

I learned that passive monitoring has limits. Wireshark can only show traffic available at the capture point, and encryption prevents it from automatically showing the contents of HTTPS communication.

## BlueHydra

I chose BlueHydra for the Bluetooth scenario because it can discover and track both Classic Bluetooth and Bluetooth Low Energy devices over time.

It could help identify unfamiliar devices nearby, but seeing a device does not prove that it is attacking anything. More evidence would be needed before deciding that a device is malicious.

## JADX

I chose JADX for reviewing an Android application when the original source code is unavailable. JADX can decompile APK and DEX files and produce readable Java-like code for review.

The recovered code is not exactly the same as the developer's original source code. It may also be harder to understand if the application was obfuscated. Even with those limits, it can help a reviewer examine the application's logic and look for insecure behavior.

## What I Learned

The biggest difference in the network scenarios was active scanning versus passive monitoring. Nmap sends traffic to find hosts and services, while Wireshark observes traffic that is already available to capture. I also learned that choosing a tool is only part of the process; I need to understand what the tool can confirm and what its results cannot prove.
