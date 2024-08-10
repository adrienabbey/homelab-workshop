# What is a Homelab?
> https://linuxhandbook.com/homelab/

- In short, a homelab is a server that you have in your home that hosts applications and VMs for testing, development, and personal use.
- I setup my own homelab many years ago, and have been using it ever since.  I self-host many different applications and services I use daily, and regularly use my homelab to try new technologies and test new ideas.  To say that my homelab has been central to my learning experience would not be an understatement.
- I feel that a lot of students would benefit from having their own homelabs.  It would give them a platform on which they can continuously learn on their own, which can help them improve their career path tremendously.  Just as importantly, it can help students become even more invested in what they're learning and doing.
- This could also benefit ACM and Wright State, as it could bring a lot of students together and foster a community among the CS, CEG and IT majors and others.

# The Goal
- Take the theoretical concepts taught in classes and turn them into practical projects students can apply and use *themselves, now*.
- Homelabs are great learning environments.  By giving students the knowledge and skills needed to get started with their own homelabs, they can start learning on their own, in a safe environment.
	- Students can learn a *lot* just by being able to *break* things (safely), then trying to figure out how to fix it.

## Example Applications
- **OpenWRT**
	- Gives students hands-on experience with open-source networking on affordable devices.
	- Wireshark, enabling secure remote access to home network
- **Proxmox**
	- Mature open-source Hypervisor
	- Supports the ZFS file system.
		- Snapshots!  Take a snapshot of a VM, do something risky, then revert it.
		- Deduplication, compression, encryption, etc.
	- VM templates.  Quickly spin up a new VM image from a template.  Pairs well with Ansible.
	- LXC containers?  I really should learn about these.
- **Nextcloud**
	- File sync, calendar, task list, and more.
- **Pihole**
	- DNS level adblock.  Pairs well with OpenWRT and Wireguard.
- **MediaWiki**
	- Private wiki to build a library of documentation
- Samba (NAS)
- Game Servers
- **Ansible**
	- Configuration management, which pairs well with VM templates.
- **Let's Encrypt**.  Getting students familiar with domain certificates and how HTTPS.

# The Homelab Workshop In Action
- I was thinking this project could become a weekly or bi-weekly workshop, where I hold lectures and guide students through these different concepts, with the goal being to help them make incremental steps towards a fully functional homelab with various services.
- Ideally, students would have access to their own hardware that they can use to work along with me during lectures.
- This could start small, perhaps with a pilot program during the first semester, to see how well this will work out, and build interest.  I don't expect a large turnout initially.
- Incentives beyond learning could include being able to take ownership of the hardware after completing the full lecture course.  This of course would be if budget permits.
- Advertising and planning will be necessary.  Nobody will show up if they don't know about it, and planning will be required to get the hardware, figure out networking, budgeting, etc.

# Requirements
## Hardware
- Ideally, I'd like to see students get two pieces of hardware: a router running OpenWRT (or OPNsense), and a server running Proxmox.
- These do NOT need to be expensive items!  These could simply be old client PCs that the university might have excess stock of, or bought used online.  Students could also provide their own hardware.
	- Minimum requirements (Proxmox): 16 GB RAM, 128 GB SSD, Virtualization-enabled CPU
	- Recommended: More than one disk drive, more RAM, more storage.
- One idea: we provide the hardware to learn in workshops on campus, and if students finish the workshop with regular attendance and meeting certain goals, they get to keep the hardware.
- If lacking the budget, we can fall back on either Rasberry Pi's (with containerization) and/or asking students to BYOD.

## Networking
- Ideally, I'd like to help students get started with the networking side, learning how to setup their own private networks, and more importantly, how to setup Wireshark to access their homelab network while away from home.
	- A key point of this project is to create something that students
- Ideally, I'd like to get students comfortable using SSH and web interfaces to manage their devices, meaning these devices will be intended to be 'headless' most of the time.
	- The sticking point here is going to be campus WiFi.  By design, this does not normally allow devices to communicate with their peers.  This makes headless administration very difficult.
	- Getting port forwarding for Wireshark will also be a very significant issue.  It's hard to properly and securely access devices on the campus network remotely.
	- This will obviously require some coordination with CATS and others to see if we can find a solution that does not cross any boundaries.
- Ideally, we want to create a homelab that students can use, even in the student dorms on campus.  Port forwarding is going to be sticking point here, again.
	- Possible circumvention: a shared cloud proxy that enables NAT punch-through for students.  This will require some semi-permanent service, investment, and technical knowhow.  And of course, making sure we aren't violating any CATS or campus rules saying we shouldn't be doing this sort of thing.
- Should this networking side of things prove unfeasible, we can simply focus on Proxmox/containerization.

## Student Skills
- Ideally, this will target students who have finished CEG-2350 (OS Concepts and Usage), but I'm inclined to make this a soft recommendation rather than a hard requirement.  I learned all of this on my own, and feel that anyone properly motivated will be able to accomplish the same.