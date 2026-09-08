# Kali Linux Fundamentals

A hands-on introduction to Linux administration and security-tool selection in a Kali Linux lab environment. This project demonstrates how I inspect a host, interpret basic network information, navigate the filesystem, work with environment variables, and reason about permissions. It also documents how I would select security tools for common defensive and investigative scenarios.

> **Ethics and scope:** All commands were used in an authorized lab environment. Network examples use documentation-only addresses. No credentials, student identifiers, private host details, or original course materials are included.

## Why this project matters

Linux and networking fundamentals are essential in a Security Operations Center (SOC). Analysts regularly inspect host state, review interfaces and routes, resolve domains, interpret permissions, and choose the right tool without altering evidence or creating unnecessary network noise.

## Skills demonstrated

- Linux command-line navigation and system inspection
- IPv4 addressing and subnet interpretation
- DNS resolution and network-interface inspection
- Filesystem and disk-usage analysis
- Shell environment variables and executable search paths
- Linux ownership and permission reasoning
- Active reconnaissance versus passive monitoring
- Security-tool selection for forensics, networking, Bluetooth, and Android analysis
- Clear technical documentation and evidence sanitization

## Project contents

| File | Purpose |
| --- | --- |
| [Linux fundamentals](linux-fundamentals.md) | Commands, observations, and security relevance from the hands-on exercises |
| [Kali tools overview](kali-tools-overview.md) | Tool-to-task decisions for five security scenarios |
| [Lessons learned](notes/lessons-learned.md) | Key takeaways and next steps for deeper SOC practice |
| [Screenshots guide](screenshots/README.md) | A safe checklist for adding selected lab evidence |

## Highlights

### Host and network awareness

I used standard Linux utilities to inspect boot time, kernel information, storage, interfaces, DNS results, and the current working directory. Rather than treating the output as a checklist, I connected each command to an analyst use case such as validating a reboot, identifying network context, or checking available storage before collecting evidence.

### Permission behavior

I created a temporary file, changed its owner to `root` with elevated privileges, verified the result, and examined why a user may still delete that file from a user-owned directory. The exercise reinforced that deletion is governed primarily by permissions on the containing directory, not only by ownership of the file.

### Security-tool selection

I evaluated tools for forensic acquisition, active service discovery, passive packet analysis, Bluetooth discovery, and Android decompilation. These were scenario-based selections; this project does not claim that every listed tool was executed.

## Example workflow

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

Outputs are intentionally omitted because they can expose usernames, hostnames, IP addresses, and lab infrastructure. Sanitized screenshots can be added by following the [screenshots guide](screenshots/README.md).

## What I would build next

The next iteration will turn these fundamentals into a small SOC investigation: generate benign authentication activity, forward logs to Wazuh or Splunk, identify failed-login patterns, and document the triage process with a timeline and detection notes.

## Responsible-use note

Reconnaissance and analysis tools should only be used on systems and networks you own or are explicitly authorized to test.
