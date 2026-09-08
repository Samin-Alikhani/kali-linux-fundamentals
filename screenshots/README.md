# Screenshot Guide

This folder intentionally contains no lab screenshots yet. Add only images that strengthen the project and have been sanitized first.

## Recommended evidence

- Boot-time inspection (`uptime -s`)
- Network-interface inspection (`ip addr`) with addresses and identifiers redacted
- Filesystem-capacity review (`df -h`)
- Kernel-version inspection (`uname -r`)
- Ownership verification (`ls -l temp.txt`) with usernames redacted if desired

Three to five strong screenshots are enough. Tool-selection scenarios do not need screenshots because they were research exercises rather than executed demonstrations.

## Sanitization checklist

Before committing an image, inspect the entire terminal window and remove or cover:

- Student or university identifiers
- Passwords, tokens, API keys, and command history containing secrets
- Real names, usernames, email addresses, and profile photos
- Public or private IP addresses that reveal the lab environment
- Hostnames, VM names, MAC addresses, interface identifiers, and university infrastructure
- Browser tabs, notifications, filenames, or background windows with personal information

Crop to the relevant command and output. Use an opaque redaction, not blur or translucent markup. Re-open the exported image and zoom in to verify that covered text cannot be recovered visually.

## Suggested filenames

```text
01-boot-time.png
02-network-interface-sanitized.png
03-filesystem-capacity.png
04-kernel-version.png
05-ownership-change-sanitized.png
```

After adding an image, reference it from the relevant section using descriptive alternative text:

```markdown
![Sanitized output showing the system boot-time check](screenshots/01-boot-time.png)
```
