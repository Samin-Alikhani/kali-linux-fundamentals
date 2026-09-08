# Linux Fundamentals Walkthrough

This write-up summarizes the hands-on concepts practiced in an authorized Kali Linux lab. It focuses on what each command reveals and why the information matters to a security analyst. Machine-specific output has been omitted for privacy.

## 1. Check system boot time

```bash
uptime -s
```

`uptime -s` reports when the system was last started. During incident triage, this can help an analyst determine whether a host rebooted near the time of an alert or whether volatile evidence may have been lost.

## 2. Inspect network interfaces and addressing

```bash
ip addr
ip route
```

`ip addr` displays interface state and assigned addresses. `ip route` shows how the host reaches local and remote networks. Together, they establish the host's network context before troubleshooting or authorized testing.

An address such as `192.0.2.25/24` means that the first 24 bits identify the network. In this documentation-only example, the network is `192.0.2.0/24`. Modern documentation generally uses CIDR notation instead of legacy classful terms such as "Class C."

## 3. Review filesystem capacity and directory usage

```bash
df -h
du -sh <directory>
```

`df -h` summarizes capacity and free space for mounted filesystems. `du -sh` summarizes how much space a specific directory consumes. This distinction matters when an analyst needs to determine whether a filesystem is full or which collection directory is using the space.

## 4. Identify the running kernel

```bash
uname -r
```

The kernel release is useful when checking compatibility, patch status, or exposure to a version-specific vulnerability. A version match alone does not prove vulnerability; distribution patches and configuration also matter.

## 5. Perform a DNS lookup

```bash
dig example.com
```

DNS lookup output can show returned records, the responding resolver, and response metadata. In SOC work, analysts use this information to investigate suspicious domains, validate name resolution, and compare observed infrastructure. `example.com` is used here to avoid exposing lab-specific domains.

## 6. Understand the Linux filesystem hierarchy

Important locations include:

| Path | Typical purpose |
| --- | --- |
| `/` | Root of the filesystem hierarchy |
| `/home` | Regular users' home directories |
| `/etc` | System-wide configuration |
| `/var/log` | Many system and service logs |
| `/tmp` | Temporary files |
| `/usr/bin` | User-facing executable programs |
| `/root` | Root user's home directory |

For security work, `/var/log` and `/etc` are especially relevant because they commonly contain event evidence and system configuration.

## 7. Identify the current working directory

```bash
pwd
```

`pwd` prints the current working directory. Confirming location before changing or deleting files reduces operational mistakes.

## 8. Inspect environment variables

```bash
echo "$SHELL"
printf '%s\n' "$PATH"
```

An environment variable is a named value that provides configuration or context to the shell and other programs. `SHELL` usually identifies the account's configured login shell. `PATH` is an ordered list of directories searched when a command is entered without a full path.

From a security perspective, an unsafe or unexpectedly modified `PATH` can cause the wrong executable to run. Quoting expansions and reviewing the order of directories are useful habits.

## 9. Reason about ownership and deletion

The lab used a temporary file to examine privilege and directory permissions:

```bash
touch temp.txt
ls -l temp.txt
sudo chown root temp.txt
ls -l temp.txt
rm temp.txt
```

Changing a file's owner to `root` requires elevated privileges. Deleting the root-owned file may not require `sudo` when the current user has write and execute permissions on the containing directory. Deletion removes a directory entry, so directory permissions are central to the decision.

The test file was disposable and contained no data.

## Analyst takeaway

The commands are simple, but the reasoning transfers directly to SOC work: establish host context, interpret results carefully, understand what an action changes, and document only the evidence needed for the investigation.
