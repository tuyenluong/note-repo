---
Creation_date: 2024-03-18 20:29
Modification_date: Monday 18th March 2024 20:29:13
Indexes:
  - "[[linux_download_install_configure]]"
---

----

# Red Hat Enterprise Linux Installation Guide

## Prerequisites

Before you begin, ensure you have the following:

1. A valid Red Hat subscription for access to the RHEL ISO and updates.
2. The RHEL installation ISO file downloaded from the Red Hat Customer Portal.
3. A bootable USB drive or a CD/DVD with the RHEL ISO burned onto it.
4. A system meeting the minimum hardware requirements for RHEL.
5. Backup any important data from your system, as the installation may overwrite existing data.

## Installation Steps

### Step 1: Create Bootable Media

- **Using a USB Drive**:
    - Use a tool like `Rufus` (Windows) or `dd` command (Linux) to create a bootable USB drive.
    -  Replace `/path/to/rhel.iso` with the path to your downloaded RHEL ISO file and `/dev/sdX` with the correct USB device.
    - Example for `dd` on Linux:
```bash
sudo dd if=/path/to/rhel.iso of=/dev/sdX bs=4M status=progress && sync
```

- **Using a CD/DVD**:
    - Burn the RHEL ISO file onto a CD/DVD using any CD/DVD burning software like `Brasero` (Linux) or `ImgBurn` (Windows).

### Step 2: Boot from Installation Media

1. Insert the bootable USB drive or CD/DVD into your system.
2. Restart the system and enter the BIOS/UEFI settings (usually by pressing a key like `F2`, `F12`, `Delete`, or `Esc` during boot).
3. Set the boot order to prioritize the USB drive or CD/DVD.
4. Save the changes and exit the BIOS/UEFI settings.

### Step 3: Start the Installation

1. Once the system boots from the installation media, you will see the Red Hat Enterprise Linux boot menu.
2. Select "Install Red Hat Enterprise Linux" and press `Enter`.

### Step 4: Language Selection

1. Choose your preferred language and click `Continue`.

### Step 5: Installation Summary

You will be presented with the Installation Summary screen where you need to configure the following:

1. **Localization**:
    - **Keyboard**: Select your keyboard layout.
    - **Language Support**: Select additional languages if needed.
    - **Time & Date**: Set your timezone.
2. **Software**:
    - **Installation Source**: The source should already be set to the local media (your bootable USB or CD/DVD).
    - **Software Selection**: Choose the base environment (e.g., `Server with GUI`, `Minimal Install`, etc.) and additional software as required.
3. **System**:
    - **Installation Destination**: Select the disk where you want to install RHEL. Configure partitioning if needed.
    - **Kdump**: Leave enabled unless you have specific reasons to disable it.
    - **Network & Hostname**: Configure your network settings and set the system hostname.

### Step 6: Begin Installation

1. After configuring all the necessary settings, click `Begin Installation`.
2. While the installation is in progress, you can set the `Root Password` and create a new user account.

### Step 7: Complete Installation

1. Once the installation is complete, you will see a message to reboot the system.
2. Remove the installation media and reboot the system.

### Step 8: Post-Installation

1. Log in using the root account or the user account you created during the installation.
2. Register your system with Red Hat using the `subscription-manager` tool:
```bash
sudo subscription-manager register --username <your-username> --password <your-password>
```
3. Attach your subscription:
```bash
sudo subscription-manager attach --auto
```
4. Update your system:
```bash
sudo dnf update -y
```

### Step 9: Additional Configuration

1. Configure additional repositories if needed.
2. Install any additional software packages you require using `dnf`.
3. Configure your system as per your needs (firewall, SELinux, network services, etc.).

---

By following these steps, you should be able to successfully install Red Hat Enterprise Linux on your system. If you encounter any issues or need further assistance, consult the Red Hat Customer Portal.






