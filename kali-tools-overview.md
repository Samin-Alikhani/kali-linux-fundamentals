# Kali Security Tools: Scenario-Based Selection

This section documents tool-selection reasoning from the research portion of the lab. It does not claim that each tool was executed. Commands and examples are limited to authorized environments.

## Tool map

| Scenario | Tool | Why it fits | Important limitation |
| --- | --- | --- | --- |
| Preserve a drive for later analysis | Guymager | Creates a forensic image so analysis can occur on a copy rather than the original device | Imaging does not decrypt protected data; chain of custody and hashing still matter |
| Find an HTTPS service on an authorized subnet | Nmap | Actively identifies hosts with TCP port 443 open | Active probes may be logged or trigger alerts |
| Observe HTTPS-related traffic passively | Wireshark | Captures and filters visible packets without probing target hosts | Visibility depends on network position; encryption hides application content |
| Discover nearby Bluetooth devices over time | BlueHydra | Tracks Classic Bluetooth and Bluetooth Low Energy devices | Discovery does not prove that a device is malicious |
| Review compiled Android application logic | JADX | Decompiles APK/DEX bytecode into readable Java-like code | Reconstructed output is not the exact original source and may be obfuscated |

## 1. Guymager: forensic acquisition first

When a storage device may contain evidence, the first priority is preservation. Guymager can create a bit-for-bit forensic image in common evidence formats. Analysis should then occur on a verified copy, reducing the chance of changing the original media.

**Decision principle:** acquire and verify first; analyze second.

## 2. Nmap: active discovery

Nmap is appropriate when an authorized tester needs to determine which hosts expose a particular service. A conceptual scan of a documentation-only `/24` network for HTTPS would be:

```bash
nmap -p 443 192.0.2.0/24
```

The scan asks which reachable hosts listen on TCP port 443. An open port suggests a service is accepting connections, but it does not by itself establish that the service is secure, vulnerable, or even HTTPS.

## 3. Wireshark: passive packet analysis

Wireshark can inspect traffic visible from the capture point. A display filter such as the following narrows the view to traffic using TCP port 443:

```text
tcp.port == 443
```

This can help identify endpoints communicating over the expected port without sending scan probes. Passive does not mean invisible in every operational sense, and switched networks may limit what a workstation can observe.

## 4. BlueHydra: Bluetooth discovery and tracking

BlueHydra is designed to discover and track nearby Classic Bluetooth and Bluetooth Low Energy devices over time. It can support situational awareness by showing repeated or unfamiliar nearby devices, but further evidence is required before labeling any device as an attacker.

## 5. JADX: Android decompilation

JADX converts compiled Android DEX bytecode into a readable Java-like representation. A reviewer can use that output to look for suspicious logic, insecure storage, hard-coded secrets, excessive permissions, or unsafe network behavior. Obfuscation and compiler transformations can reduce readability, so findings should be validated with other static or dynamic techniques.

## Active versus passive collection

- **Active reconnaissance** sends traffic to a target to elicit a response. Nmap is the example in this lab.
- **Passive monitoring** observes traffic available at the capture point. Wireshark is the example in this lab.

The correct approach depends on authorization, objectives, network visibility, evidence-handling requirements, and the risk of disrupting or alerting the environment.
