# EVE‑NG Setup Guide

This folder contains everything you need to **install, configure, and prepare your EVE‑NG environment** to start using the Advanced Networking labs.

Below is a concise setup guide referencing the process shown in the **installation video**:  
🎥 [**How to Install EVE‑NG**](https://youtu.be/ydDGVFkvGsU)

---

## What This Guide Covers

This setup guide walks you through:

*   Preparing your virtualization platform
*   Installing EVE‑NG (Community Edition)
*   Accessing the web interface
*   Uploading Cisco IOS/QEMU/IOL images
*   Verifying your initial lab environment

These are the essential first steps before importing and running any lab topologies.

---

## Step 1: Prepare Your Virtualization Platform

Before anything else, decide where you will run EVE‑NG:

**Supported options include:**

*   **VMware Workstation** (Windows/Linux)
*   **VMware ESXi**
*   **Bare‑metal install**
*   **Other hypervisors that support ISO/OVA installs**

Make sure:

*   **VT‑x / AMD‑V virtualization support is enabled** in BIOS/UEFI
*   You allocate **sufficient resources**
    *   ≥ 8 GB RAM (more is better for multi‑device labs)
    *   Multiple CPUs
    *   At least 40 GB of disk space

Good resource planning here saves troubleshooting later.

---

## Step 2: Download and Install EVE‑NG

1.  Get the **EVE‑NG Community Edition ISO** from the official site:  
    [EVE-NG ISO](https://www.eve-ng.net/index.php/downloads/community/)
2.  Deploy the ISO to your virtual platform or install the VM directly (OVA if available).
3.  Boot the VM and complete the initial configuration (network settings, hostname, etc.).

**Default credentials:**
*   Console login: `root` / `eve`
*   Web UI login: `admin` / `eve`

This gives you access to the EVE‑NG dashboard via a browser.

---

## Step 3: Access the EVE‑NG Web Interface

Open your browser and navigate to the EVE‑NG web GUI IP address shown after the VM boots.  
Login with:

*   **Username:** `admin`
*   **Password:** `eve`

You should now see the EVE‑NG dashboard where labs are managed.

---

## Step 4: Upload Cisco Images

To run network devices (Cisco routers/switches) in EVE‑NG you must upload images.

1.  Connect to the EVE‑NG VM via **SFTP** ([WinSCP](https://winscp.net/eng/download.php), [FileZilla](https://filezilla-project.org/)).
2.  Download the Images from [Google Drive](https://drive.google.com/file/d/1OIBchx85RLvKP9Hf6fjxtyh3PWzuovsl/view?usp=sharing)
3.  Transfer your Cisco IOL images into:
    `/opt/unetlab/addons/iol/bin/`
4.  On the EVE‑NG VM shell, run the permission fix command:
    ```
    /opt/unetlab/wrappers/unl_wrapper -a fixpermissions
    ```
    This ensures EVE‑NG can read the images properly.

Once done, return to the web GUI to create your first lab and use these images.

---

## Step 5: Verify Your Setup

Before you start networking labs:

1.  Ensure images show up when adding a node.
2.  Confirm you can power on a device.
3.  Open the console via HTML5.
4.  Ping between devices inside a tiny test topology.

If this works, your Advanced Networking labs will run smoothly.

---

## Recommended Tools

You might find the following useful:

*   **SFTP client:** [WinSCP](https://winscp.net/eng/download.php), [FileZilla](https://filezilla-project.org/)
*   **Terminal/CLI:** [Putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html), SecureCRT
*   **Wireshark** (optional for deeper packet analysis)

---

## Additional Notes & Configuration

### Wireshark Integration (Windows)
After installing the EVE‑NG [Client Pack](https://customers.eve-ng.net/EVE-NG-Win-Client-Pack-3.0.exe):

1.  Navigate to: `C:\Program Files\EVE-NG\`
2.  Open Command Prompt in this folder.
3.  Run:
    ```
    plink.exe -ssh -pw eve root@<EVE-NG-IP>
    ```
    This enables Wireshark packet capture from the EVE‑NG web interface.

### Fixing Image Permissions
After uploading images to EVE‑NG:

1.  Access the EVE‑NG VM (SSH or console).
2.  Login as root.
3.  Run:
    ```
    /opt/unetlab/wrappers/unl_wrapper -a fixpermissions
    ```
    **This step is mandatory for images to work correctly.**

---

**Notes:**
*   This guide assumes a Community Edition install.
*   If you are using Pro / Learning Center editions, licensing and feature access may differ.
*   For official EVE‑NG documentation and installation details, see:  
    [EVE-NG Documentation](https://www.eve-ng.net/index.php/documentation/installation/)

Once this is done, you’re ready to import the labs in the Advanced Networking modules and start building/validating real network scenarios.
