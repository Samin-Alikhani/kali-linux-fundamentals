# Lessons Learned

This lab helped me connect basic Linux commands with the information they provide about a system. My main takeaways were:

- `ip addr` shows network interfaces and their assigned addresses.
- CIDR notation such as `/24` is more useful today than older terms such as "Class C."
- `df` reports space for mounted filesystems, while `du` measures the space used by files or directories.
- `PATH` tells the shell where to search for commands.
- Changing the owner of a file requires elevated privileges, but deleting a file depends mainly on the permissions of its containing directory.
- Nmap performs active scanning, while Wireshark can be used for passive traffic analysis.
- A drive should be imaged before forensic analysis so the original evidence is not changed.
- Decompiled Android code is a reconstructed version of the application, not the exact original source code.

The lab also reminded me to be precise when describing my work. I should clearly separate tools I actually used from tools I only researched for a scenario.

## Next step

My next goal is to apply these Linux and networking fundamentals in a small log-analysis project. I would like to generate test authentication activity, review the resulting logs, and document how I identify and investigate failed login attempts.
