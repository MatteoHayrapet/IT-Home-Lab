# Lab 4 — Imaging, Cloning & Disk Partitioning

**Cert objectives:** A+ Core 1 (disks/partitioning), A+ Core 2 (deployment, imaging)

## Objective
Learn how IT deploys many identical machines from a single source ("golden image"), and practice the disk-management skills behind setting up storage.

## What I Did
**Cloning / imaging:**
- Full-cloned the `Win11-Lab` VM into an independent second machine.
- Selected **"Generate new MAC addresses"** so the clone got a unique hardware identity.
- Ran `ipconfig /all` on the clone and compared the MAC against the original to confirm they were distinct.

**Disk partitioning (Disk Management):**
- Shrank the `C:` volume by 10 GB, creating unallocated space.
- Created a **New Simple Volume** from that space.
- Formatted it **NTFS**, assigned drive letter **E:**, and labeled it `LabData`.
- Confirmed the new drive appeared in *This PC*.

## What I Learned
- The **golden-image / cloning** concept behind mass deployment.
- Why every network adapter needs a **unique MAC**, and what happens if clones share one.
- **Sysprep** — why real deployments strip the computer name and unique IDs so each machine is distinct (my clone kept the original's hostname, which would conflict on a real network).
- Why the clone kept the same IP: VirtualBox **NAT** gives each VM its own isolated network, so `10.0.2.15` doesn't collide.
- The full partitioning workflow: **shrink → create → format NTFS → assign drive letter.**
- In Disk Management, **black = unallocated space.**

## Resume-Ready Summary
> Performed system imaging and disk management in a virtualized lab — full-clone deployment with unique MAC addressing, plus volume shrink, partition creation, NTFS formatting, and drive-letter assignment.
