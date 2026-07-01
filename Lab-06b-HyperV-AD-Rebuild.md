# Lab 6b — Active Directory on Hyper-V (Migration + Rebuild)

**Goal:** Migrate the domain lab from Oracle VirtualBox to Windows Hyper-V, and rebuild the full `mhlab.local` domain from scratch — driving the entire process through PowerShell instead of GUI wizards.

**Why:** Hyper-V is a Type 1 (bare-metal) hypervisor and is the virtualization platform Azure runs on. For a cloud-security career path, hands-on Hyper-V time maps directly to real-world and cloud environments. Building via PowerShell develops the automation muscle that GUI-only workflows never do.

---

## Environment

| Item | Value |
|------|-------|
| Host OS | Windows 11 Pro (25H2, build 26200) |
| Hypervisor | Hyper-V (enabled via Windows Features) |
| Server VM | `Server2025-DC`, **Generation 2** (UEFI + Secure Boot) |
| Server OS | Windows Server 2025 (Desktop Experience), 180-day eval |
| vCPU / RAM | 6 vCPU / 4 GB startup, 2 GB min (Dynamic Memory) |
| Disk | 60 GB VHDX |
| Virtual switch | `lab-net` (Private) |

---

## Domain

| Item | Value |
|------|-------|
| Domain (FQDN) | `mhlab.local` |
| NetBIOS | `MHLAB` |
| Domain controller | `DC01` |
| DC IP | `192.168.10.10` /24 |
| Gateway | `192.168.10.1` (convention; no router on Private switch) |
| DNS | `127.0.0.1` (DC points at its own DNS) |
| OUs | `IT`, `Sales` |
| Group | `IT-Staff` (Global / Security, in IT OU) |
| User | `jtech` (in IT OU, member of IT-Staff) |

---

## Steps completed

1. Enabled the Hyper-V feature on Windows 11 Pro; confirmed Hyper-V Manager.
2. Created a **Private** virtual switch named `lab-net` (isolated lab network).
3. Created a **Generation 2** VM and installed Windows Server 2025 (Desktop Experience).
4. Set Dynamic Memory floor (min 2 GB) so AD is never starved.
5. Renamed the server to `DC01` in PowerShell (`Rename-Computer`).
6. Set static IP / prefix / gateway (`New-NetIPAddress`) and self-pointing DNS (`Set-DnsClientServerAddress`).
7. Installed the AD DS role (`Install-WindowsFeature`).
8. Promoted to first DC of a new forest (`Install-ADDSForest`) — created `mhlab.local`.
9. Built OUs, group, and user, and set group membership — all in PowerShell.
10. Verified via `Get-ADDomain`, `Get-ADUser`, `Get-ADGroupMember`, and the `dsa.msc` GUI.

---

## Concepts reinforced

- **AD and DNS are inseparable.** A DC runs its own DNS and is the authority for its domain; clients find the domain *through* DNS. Mispointed DNS is the #1 cause of failed domain joins.
- **Static addressing rationale.** Private ranges, `/24` sizing, `.1` gateway convention, loopback (`127.0.0.1`) for a self-hosting DNS server.
- **GUI vs. terminal.** GUI is for exploring; the terminal is for doing it again — repeatable, scriptable, and the only option on headless / cloud servers. (`dcpromo` is retired; PowerShell is the current promotion method.)
- **Gen 2 VMs** use UEFI + Secure Boot, matching modern and cloud servers.

---

## Artifacts

- `Rebuild-Domain.ps1` — phase-by-phase script that stands up the entire domain from a fresh server. Reusable "rebuild from zero" tool.

---

## Next up

- **Lab 6c:** Build a Windows 11 client VM on `lab-net`, point its DNS at `192.168.10.10`, and join it to `mhlab.local`; verify `MHLAB\jtech` login.
- **Then:** Hyper-V-only capabilities — checkpoints, VLAN tagging on virtual switches, nested virtualization.
- **Lab 7:** pfSense (firewall/router, VLANs, DHCP, segmentation).
