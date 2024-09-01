# Lesson Plan (tentative)
- This workshop series will likely be split into several parts spread across the entire semester.
- This document is intended to only serve as a springboard to build upon as I figure things out.  
    - Circumstances will change, the number of attendees will likely change over time, and their interests will likely determine what I teach.

## Sticking Points
- Focus: should it be Proxmox?  Should I VPN?
    - Half my plans hinge on Proxmox, which is a headless server.
    - The other half of my plans hinge on having VPN access.
    - My entire goal at first was to focus on making a *usable* homelab environment.  The fact that many students live on campus complicates these plans.
    - A key point of a homelab, in my mind, is to be able to run services 24/7 that are accessible from anywhere.
        - Running a desktop-focused distro without a VPN complicates this immensely.
- Networking:
    - I like headless servers.  Proxmox is designed with this in mind, offering a web interface out of the box for system management.
    - This means students will need both the hardware to run the server and a separate device to manage it.
    - This also means that students will need network access to that device.
    - Many headless servers do not offer easy WiFi configuration services.  This is further complicated by the fact that the university's network likely does not allow peer-to-peer communication between wireless devices.
    - Ideal solution: network switches, with Ethernet connections for each device.  Additionally, a wireless access point which students can connect to that allows for communication between all devices connected.
- Non-Proxmox distros.  I'll need to familiarize myself with KVM/Qemu on Ubuntu distributions.  All my experience is with Proxmox (and to a lesser degree, Hyper-V).

## Announcement Plans
- BYOD, with old laptops available?
- Make it *VERY* clear that any data on the devices brought will be *lost* when installing Linux.
    - Dual-boot is possible, but not something I want to personally support.  Students are allowed to do as they please, but I cannot be held responsible for any lost data due to their actions.
- Hardware requirements: 
    - AMD/Intel CPU with virtualization enabled (no ARM, no Chromebook, no Macs, etc.)
        - Again, while these may be viable platforms, they are outside the scope of what I want to support.
        - While a Raspberry Pi is also viable, it doesn't support virtualization, which is something I want to focus on.
    - Recommended: 
        - Core i5 / Ryzen 5 or better
        - 256 GB or more of SSD storage
        - 16 GB or more RAM
    - Secure Boot note: Many Linux distros do not support secure boot out of the box.  This may need to be disabled.

## Day 1: Introduction, Linux Installation
- Preparation: 
    - Prepare routers around the room to allow students to attach their devices to them (Ethernet and WiFi).
    - Prepare USB flash drives for installation media.
- The core of the homelab is going to be Linux and virtualization.  Linux servers are everywhere, and are excellent at what we're doing, with zero cost.  Win-win-win.
- There's *many* ways to do a homelab.  I'm going to focus on what *I'm* familiar with, and adapt as needed.
- OSes: Proxmox (preferred), Ubuntu, others.
    - I'll need to clearly state that while anyone can install any distribution of their choice, I can only support those I'm familiar with (Debian derivatives mostly).
    - There may be other students in attendance who may be familiar with other distributions.
    - Point out that Proxmox is intended to run as a *headless* server.  This means it is designed to be managed by another device on the network using a web interface.
        - That said, everything *can* be done from the command line.  I'm not too experienced with this, however.
- Step -1: Demonstration and Bookmark
    - Demonstrate my homelab, show what I'm currently using it for.  Grab attention, get people invested.
    - Point people to this Github repo and encourage them to bookmark it.
- Step 0: Warnings.
    - This *will* result in data loss.  Backup, backup, backup.  Storage will get wiped.
    - There are zero guarantees this will work flawlessly for everyone.  If it were easy, there would be far fewer IT jobs.  While Linux has matured a great deal, it's still behind Windows in hardware support.
    - This includes any data on the USB flash drives!
- Step 1: Hardware preparation.
    - Connect devices.  Turn them on.
- Step 2: BIOS/UEFI configuration.
    - Common keys to enter BIOS setup include `DEL`, `F10`, and `F2`.
    - Enable Virtualization.
    - Enable boot from USB.
    - Some BIOSes might need to enable the boot menu.
    - Some Linux distros will require disabling Secure Boot.
- Step 3: Installation media creation.
    - Download distro of choice.
    - Rufus is a great choice for Windows users.
    - I'm going to assume that those already running Linux can figure out how to make installation media.
    - Do the needful.
- Step 4: Boot from USB, begin Installer.
    - Common keys to select which device to boot from include `F12`.
- Step 5: Installer options.
    - Timezone: `Americas \ New York`
    - Encourage `ZFS`, as it is stable, modern, and enables snapshotting among other great features.
    - *Be mindful of IP configuration*!  If the installer defaults to a static IP address, people at each table need to change the IP to something unique.
        - Also be mindful that DNS did not automatically configure for my proof-of-concept.
    - Ensure installation completes.
- Step 6: Boot into new installation.
    - Note that the device's IP and port will be listed after booting.  Write this down and/or take a picture of this if needed.
    - Login with `root` and the password configured during installation.
    - Run `apt update` and `apt full-upgrade`.
        - Note: Because we're on root, `sudo` isn't a thing!
        - Note: The enterprise repo is enabled by default.  This will be fixed soon!
        - Ensure this is successful.  If it fails, it suggests that network settings need adjusting.
- Step 7: Connect to the web interface.
    - Login with `root`
    - Ensure everything is updating.
    - Disable the Enterprise repo, and enable the Free repo.
- Step X: Plug ACM.
    - Discord, Engage, and ACM membership.
        - Announcements of upcoming events will show here.
    - Because we need members.  And we're awesome.
    - Encourage active participation.  Point out that we take recommendations for future event ideas.

## Day 2: Virtualization

## Day 3: VM Templates, Ansible?

## Day 4: Nextcloud

## Day X: Networking
- This is going to be complicated, and require a lot of planning and preparation to properly execute.
- It's easy to forget just how nice it is to have full ownership and control over your own home network.
- A key point to making a homelab *usable* outside your home is to have a secure VPN connection to your home network.