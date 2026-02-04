# Task 1.1 — The Linux Migration

## Purpose
- Install and configure a Linux environment so you understand the software runtime and can control the platform where your tools run.
- This document explains what to do, how to approach it safely, and where to find authoritative guidance. It does not include copy-paste commands or full scripts; implement the steps yourself and consult the official documentation linked below.

## Outcome expectations
- Choose one of the following tiers:
  - Gold: Install Linux as a dual-boot alongside Windows.
  - Silver: Install and configure WSL2 (Windows Subsystem for Linux).
  - Bronze: Install Linux in a VM or via a persistent live USB.
- Deliverable: evidence that a system-info tool such as `neofetch` ran in your terminal (for example, a screenshot) and a short README describing choices and verification steps.

## Important safety note
- Back up important files to external storage before modifying partitions or installing a new OS.
- If you are unfamiliar with partitioning or bootloader concepts, consider using a VM or WSL2 until you are comfortable.

## Choose a distribution
- Pick a beginner-friendly distribution and consult its install guide:
  - Ubuntu LTS — official Ubuntu installation documentation.
  - Pop!_OS — vendor installation guide.
  - Fedora — Fedora Project installation instructions.
- Tip: check hardware compatibility, especially GPU and Wi‑Fi chipset, before selecting a distribution.

## Installation paths
- Dual-boot (Gold): provides native performance; requires resizing partitions and configuring EFI/GRUB.
- WSL2 (Silver): works well on Windows without partition changes.
- VM or Live USB (Bronze): safest option for beginners; no changes to your primary OS.

### High-level dual-boot workflow
1. Back up data and create Windows recovery media if desired.
2. Shrink the Windows partition to free space for Linux; leave at least 30–50 GB.
3. Create installation media (USB) using the distro's recommended imaging tool.
4. Boot the installer in UEFI mode and follow guided or manual partitioning options.
5. Create sensible partitions: EFI (use existing if present), root `/`, optional `home`, and swap or swap file.
6. Install the bootloader; most installers configure GRUB to detect other operating systems.
7. Reboot and verify you can select and boot both operating systems.

### High-level WSL2 workflow
1. Enable the Windows features required for WSL2 using Microsoft's documentation.
2. Install a distribution from the Microsoft Store or import an image.
3. Set WSL2 as the default and configure your shell and packages inside the distribution.
4. Configure integration with Windows terminal applications if desired.

## Post-install checks and basic setup
- Boot verification: confirm you can start the new Linux instance and, if dual-booting, that Windows still boots.
- Networking: confirm Wi‑Fi or ethernet connectivity and that you can update packages.
- Package manager: perform system updates and install basic developer tools such as `git` and a code editor.
- User configuration: create a non-root user if one was not created by the installer, set up SSH keys, and configure your shell environment.
- Terminal check: run your system-info tool and capture a screenshot showing distribution and system details.

## What to include in your submission
- Create a directory for your submission: `task/<your-github-username>/1-linux-migration/`
- Include:
  - `README.md` — 1–2 paragraphs describing the distribution, installation path, partition sizes or notable choices, and any problems you solved.
  - `neofetch-screenshot.png` or equivalent — clearly shows the distribution and system summary.
  - Optional: `post-install.txt` listing a few important commands you ran and packages you installed.

## How reviewers will verify
- Confirm the screenshot clearly shows the distribution and terminal output.
- Read your task README to ensure steps are reproducible and troubleshooting notes are included.
- If you claim dual-boot, provide a short note about how you verified both systems boot.

## Where to find authoritative help
- Official installation guides for Ubuntu, Pop!_OS, and Fedora.
- Microsoft WSL documentation.
- Distro documentation and reputable tutorials on partitioning, UEFI, and bootloader concepts such as GRUB.

## Troubleshooting tips
- If Windows does not appear in the boot menu after install, check whether an EFI entry was created and review firmware boot order.
- If Wi‑Fi or GPU drivers are missing, search for vendor-supplied drivers or community guides for your hardware model.
- When uncertain, prefer a VM or WSL2 until you are comfortable modifying disk partitions.

## Final checklist before submitting
- [ ] Backed up important data.
- [ ] Installed Linux via dual-boot, WSL2, or VM.
- [ ] Captured a clear screenshot of the system-info tool showing the distribution.
- [ ] Wrote a short `README.md` describing choices and verification.
- [ ] Placed the files under `task/<your-github-username>/1-linux-migration/` and opened a PR with verification steps.

## If you want help
- I can provide a one-page checklist template for your `README.md` or point you to official vendor pages for installer steps for the distribution and path you plan to use. Tell me which distribution and install path you plan to use and I will point you to the most relevant official documentation.