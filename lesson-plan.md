# Lesson Plan (tentative)
- This workshop series will likely be split into several parts spread across the entire semester.
- This document is intended to only serve as a springboard to build upon as I figure things out.  
    - Circumstances will change, the number of attendees will likely change over time, and their interests will likely determine what I teach.

## Sticking Points
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
- The core of the homelab is going to be Linux and virtualization.  Linux servers are everywhere, and are excellent at what we're doing, with zero cost.  Win-win-win.
- There's *many* ways to do a homelab.  I'm going to focus on what *I'm* familiar with, and adapt as needed.
- OSes: Proxmox (preferred), Ubuntu, others.
    - I'll need to clearly state that while anyone can install any distribution of their choice, I can only support those I'm familiar with (Debian derivatives mostly).
    - There may be other students in attendance who may be familiar with other distributions.

## Day 2: Virtualization

## Day 3: VM Templates, Ansible?

## Day 4: Nextcloud

## Day X: Networking
- This is going to be complicated, and require a lot of planning and preparation to properly execute.
- It's easy to forget just how nice it is to have full ownership and control over your own home network.
- A key point to making a homelab *usable* outside your home is to have a secure VPN connection to your home network.