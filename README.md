# IT Home Lab

Hands-on labs documenting my self-directed IT training. I'm an incoming Computer Information Technology (B.S.) student currently preparing for the **CompTIA A+**, building practical skills through a home lab rather than passive study. Each lab below includes what I did, what broke, and what I learned.

**Lab environment:** Windows 11 Pro running in Oracle VirtualBox (TPM 2.0, UEFI, Secure Boot), with snapshots for safe break/fix practice.

---

## Certification Roadmap

`A+` → `Network+` → `Security+` → `AWS` → Cloud Security

These labs map to objectives across that path, starting with A+ fundamentals.

---

## Labs

| # | Lab | Focus | Cert Track |
|---|-----|-------|-----------|
| 1 | [Build a Windows 11 VM](lab-01-vm-setup.md) | Virtualization, OS install, snapshots | A+ |
| 2 | [Windows Administration & Break/Fix](lab-02-windows-admin.md) | CLI diagnostics, system tools, user management | A+ |
| 3 | [Local Security: Permissions & Firewall](lab-03-local-security.md) | NTFS permissions, Windows Firewall | A+ |
| 4 | [Imaging, Cloning & Partitioning](lab-04-imaging-partitioning.md) | Deployment, disk management | A+ |

*More labs in progress — Active Directory, pfSense networking, and AWS cloud security to come.*

---

## Skills Demonstrated

- **Virtualization:** VM creation/configuration, snapshots, cloning, full vs. linked clones
- **OS Administration:** clean installs, local accounts, users & groups, permissions
- **Networking:** `ipconfig`, `ping`, reading IP/MAC/DNS/gateway, NAT, ICMP
- **Security:** NTFS Allow/Deny permissions, profile isolation, Windows Defender Firewall rules
- **Disk Management:** partitioning, shrinking volumes, NTFS formatting, drive letters
- **Troubleshooting:** reproducing and resolving real-world tickets (no-internet, boot order, blocked traffic)
