# Kali Linux Fundamentals

This project documents my hands-on practice with Linux administration and introductory security concepts in an authorized Kali Linux lab environment. I worked with system information, network configuration, filesystem navigation, environment variables, and file permissions. I also researched how several Kali tools apply to common security scenarios.

Machine-specific information and original course materials have been excluded from this repository.

## Project Overview

I built this project to strengthen my Linux and networking fundamentals. The exercises helped me move beyond memorizing commands by focusing on how to interpret their output, understand system behavior, and apply the concepts during troubleshooting and security analysis.

## Skills Demonstrated

- Linux command-line navigation and system inspection
- IPv4 addressing and subnet interpretation
- DNS resolution and network-interface inspection
- Filesystem and disk-usage analysis
- Shell environment variables and executable search paths
- Linux ownership and permission reasoning
- Active reconnaissance versus passive monitoring
- Security-tool selection for forensics, networking, Bluetooth, and Android analysis

## Project contents

| File | Purpose |
| --- | --- |
| [Linux Fundamentals](linux-fundamentals.md) | Commands, observations, and security relevance from the hands-on exercises |
| [Kali Tools Overview](kali-tools-overview.md) | Tool-to-task decisions for five security scenarios |
| [Lessons Learned](notes/lessons-learned.md) | Key takeaways and next steps for deeper SOC practice |

## Highlights

### Host and network Awareness

I used standard Linux utilities to inspect boot time, kernel information, storage, interfaces, DNS results, and the current working directory. Rather than treating the output as a checklist, I connected each command to an analyst use case such as validating a reboot, identifying network context, or checking available storage before collecting evidence.

### Permission Behavior

I created a temporary file, changed its owner to `root` with elevated privileges, verified the result, and examined why a user may still delete that file from a user-owned directory. The exercise reinforced that deletion is governed primarily by permissions on the containing directory, not only by ownership of the file.

### Security-Tool Selection

I evaluated tools for forensic acquisition, active service discovery, passive packet analysis, Bluetooth discovery, and Android decompilation. These were scenario-based selections; this project does not claim that every listed tool was executed.

## Example Workflow

```bash
# Inspect host state
uptime -s
uname -r
df -h

# Inspect network context
ip addr
ip route

# Inspect shell context
pwd
echo "$SHELL"
printf '%s\n' "$PATH"
```

Outputs are intentionally omitted because they can expose usernames, hostnames, IP addresses, and lab infrastructure. Selected screenshots may be added later after they have been reviewed and sanitized.

## Next Iteration

The next iteration will turn these fundamentals into a small SOC investigation: generate benign authentication activity, forward logs to Wazuh or Splunk, identify failed-login patterns, and document the triage process with a timeline and detection notes.
