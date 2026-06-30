# Lab 6 — Active Directory: Domain Controller & Domain Join

**Cert objectives:** A+ / Network+ (Active Directory, DNS, server roles, domain join)

## Objective
Build a small enterprise network from scratch: stand up a Windows Server as a domain controller running Active Directory, then join a Windows 11 client to the domain and authenticate a domain user across the network.

## What I Did
**Server setup:**
- Built a Windows Server 2025 (Desktop Experience) VM.
- Assigned a **static IP** (`192.168.10.10`), subnet `255.255.255.0`, with the **DNS server pointed at itself** (required for a domain controller).
- Renamed the server to `DC01` and restarted.

**Promote to domain controller:**
- Installed the **Active Directory Domain Services** role via Server Manager.
- Promoted the server to a domain controller, creating a **new forest**: `mhlab.local`.
- Set a DSRM (Directory Services Restore Mode) recovery password.

**Active Directory administration (ADUC):**
- Created **Organizational Units**: `IT` and `Sales`.
- Created a **user** account: `jtech` (John Tech).
- Created a **security group** `IT-Staff` and added `jtech` as a member.

**Join the client:**
- Placed both VMs on the same VirtualBox **Internal Network** (`lab-net`) for isolation.
- Gave the Windows 11 client a static IP (`192.168.10.20`) with its **DNS pointed at the server** (`192.168.10.10`).
- Verified connectivity with `ping` before joining.
- Joined the client to `mhlab.local` (via `sysdm.cpl`), restarted, and logged in as **`MHLAB\jtech`**.
- Confirmed the domain login with `whoami` → returned `mhlab\jtech`.

## What I Learned
- Server roles and the AD DS install / DC promotion process.
- Why a domain controller needs a **static IP** and **self-referencing DNS**.
- The difference between **OUs, groups, and users**, and how each is used.
- That a client must use the **domain controller as its DNS server** to find and join the domain — the single most common reason domain joins fail.
- Local vs. domain login (`MHLAB\` prefix) and verifying identity with `whoami`.
- Using a VirtualBox Internal Network to build an isolated, multi-VM lab.

## Resume-Ready Summary
> Deployed a Windows Server 2025 domain controller (Active Directory, DNS) and joined a Windows 11 client to the domain — including OU/user/group administration, static IP and DNS configuration, and verified cross-machine domain authentication.
