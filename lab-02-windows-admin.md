# Lab 2 — Windows Administration & Break/Fix

**Cert objectives:** A+ Core 2 (command-line tools, OS features, user management, troubleshooting)

## Objective
Get hands-on with the everyday tools a help desk technician uses — the command line, built-in system utilities, and user management — then deliberately break things and recover.

## What I Did
- Ran CLI diagnostics: `ipconfig /all`, `ping`, `hostname`, `systeminfo`.
- Located and interpreted key network values in the output: **IP address, MAC (Physical Address), DNS server, and default gateway.**
- Compared Command Prompt with PowerShell (`Get-Process`, `Get-Service`).
- Explored core system tools: **Device Manager, Event Viewer, Disk Management, Task Manager.**
- Created a local user, then **granted and revoked Administrators group membership.**
- Disabled the network adapter to reproduce a "no internet" ticket, then re-enabled it to restore connectivity.
- Used the snapshot tree to roll the VM back to a clean state.

## What Broke / How I Fixed It
After restoring a snapshot, the VM booted back into Windows Setup instead of the desktop. The cause: the install **ISO was still mounted** and sat ahead of the hard drive in the boot order. I fixed it by removing the ISO from the virtual optical drive in the VM's Storage settings — the same principle as removing a Windows install USB after installation completes.

## What I Learned
- How to read `ipconfig` output and identify IP / MAC / DNS / gateway.
- The difference between Command Prompt and PowerShell, and when each is used.
- Local user and group management.
- Using `ping` to test a connection end-to-end through the whole network chain.
- How boot order and install media interact.
- Snapshot-tree rollback.

## Resume-Ready Summary
> Performed Windows client administration and troubleshooting in a virtualized lab — user/group management, network adapter diagnostics, CLI tooling, and snapshot-based recovery.
