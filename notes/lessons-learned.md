# Lessons Learned

## Technical takeaways

- A Linux command is most useful when I can explain what its output means and how it supports an investigation.
- `ip` is the modern toolset for inspecting interfaces and routes; CIDR notation is clearer than legacy classful terminology.
- `df` answers a filesystem-capacity question, while `du` answers a file-or-directory usage question.
- `PATH` affects which executable the shell selects, so directory order and unexpected entries can have security consequences.
- File ownership alone does not determine whether a file can be deleted; permissions on the containing directory are critical.
- Active discovery and passive observation have different visibility, authorization, and detection tradeoffs.
- Forensic work begins with preserving evidence and validating the copy before analysis.
- Decompilation produces a useful reconstruction, not the developer's exact original source code.

## Documentation takeaways

- A portfolio should explain decisions and observations instead of reproducing assignment questions and answers.
- Screenshots should support a specific claim, not merely prove that a command was typed.
- Terminal evidence must be reviewed for names, identifiers, credentials, IP addresses, hostnames, and infrastructure details before publication.
- It is important to distinguish tools I used from tools I researched or selected for a scenario.

## Next steps

1. Add three to five carefully sanitized screenshots that support the strongest hands-on sections.
2. Build a small log-analysis project using Wazuh or Splunk and document an alert-triage workflow.
3. Practice explaining the ownership exercise and active-versus-passive distinction as short interview answers.

## Resume-ready project bullet

> Documented Linux host and network inspection, DNS resolution, filesystem analysis, environment variables, and ownership behavior in Kali Linux; compared active reconnaissance, passive traffic analysis, forensic acquisition, Bluetooth discovery, and Android decompilation tools for security use cases.
