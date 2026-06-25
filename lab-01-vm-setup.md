# Lab 1 — Build a Windows 11 VM in VirtualBox

**Cert objectives:** A+ Core 1 (virtualization), A+ Core 2 (OS installation)

## Objective
Set up a safe, isolated lab environment by building a Windows 11 virtual machine from scratch — the foundation for every lab that follows.

## What I Did
- Installed Oracle VirtualBox 7.2.10 and the Extension Pack (for TPM 2.0 support).
- Created a VM (`Win11-Lab`): 4 GB RAM, 2 CPUs, 80 GB disk.
- Verified the Windows 11 hardware requirements were met: **TPM 2.0, EFI, and Secure Boot** all enabled.
- Performed a clean installation of Windows 11 Pro from a Microsoft ISO.
- Created a **local account** during setup instead of a Microsoft account.
- Took a snapshot (`fresh install`) as a clean recovery point.

## What Broke / How I Fixed It
The VM failed to boot on the first attempt — a *"missing operating system / boot order"* error. The cause: it skipped past the "Press any key to boot from CD" prompt, so it never started the installer. I fixed it by re-mounting the ISO through the boot-error dialog and retrying. I also bypassed Windows 11's forced Microsoft-account requirement using the **"work or school → domain join instead"** route to create a local account.

## What I Learned
- How TPM, UEFI/EFI, and Secure Boot map to Windows 11's install requirements.
- How VM snapshots make it safe to break and restore a system instantly.
- The local-account workaround during Windows OOBE (out-of-box experience).
- Why boot order and install media interact the way they do.

## Resume-Ready Summary
> Built and configured a Windows 11 virtual machine in VirtualBox (TPM 2.0, UEFI, Secure Boot) and performed a clean OS install with snapshot-based recovery.
