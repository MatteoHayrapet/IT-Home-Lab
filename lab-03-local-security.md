# Lab 3 — Local Security: NTFS Permissions & Firewall Rules

**Cert objectives:** A+ Core 2 (NTFS permissions, Windows Defender Firewall, ICMP)

## Objective
Practice the security side of desktop support: controlling who can access what with NTFS permissions, and controlling network traffic with firewall rules.

## What I Did
**NTFS permissions:**
- Created a standard (non-admin) user, `testuser`.
- Created a folder at `C:\SecretStuff` and used the **Security** tab to set **Deny Full Control** for `testuser`.
- Logged in as `testuser` and confirmed the folder was visible but **access was denied** — verifying the permission was enforced.

**Firewall:**
- Opened **Windows Defender Firewall with Advanced Security** (`wf.msc`).
- Built a custom **Outbound Rule** blocking **ICMPv4**.
- Confirmed `ping 8.8.8.8` failed while the rule was active, then deleted the rule and confirmed ping worked again.

## What Broke / How I Fixed It
On the first attempt, `testuser` couldn't see the folder at all. The cause: I'd created it on the admin account's desktop (`C:\Users\MHLAB\Desktop`), and **each user has an isolated profile** — `testuser` only sees its own. I fixed it by moving the folder to `C:\` (a shared location) so `testuser` could navigate to it and the Deny permission could actually be tested.

## What I Learned
- NTFS permissions via the Security tab, and that **Deny always overrides Allow.**
- Per-user profile isolation as a built-in security boundary.
- **ICMP** is the protocol `ping` uses.
- How a silent firewall rule can block specific traffic while general internet access still works.
- Creating and removing outbound rules in `wf.msc`.

## Resume-Ready Summary
> Configured and tested Windows local security in a lab — NTFS file permissions (Allow/Deny), per-user profile isolation, and Windows Defender Firewall rules (ICMP), including verifying enforcement and remediation.
