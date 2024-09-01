# What is a Homelab?
> https://linuxhandbook.com/homelab/

- In short, a homelab is a server that you have in your home that hosts applications and VMs for testing, development, and personal use.
- I setup my own homelab many years ago, and have been using it ever since.  I self-host many different applications and services I use daily, and regularly use my homelab to try new technologies and test new ideas.  To say that my homelab has been central to my learning experience would not be an understatement.
- I feel that a lot of students would benefit from having their own homelabs.  It would give them a platform on which they can continuously learn on their own, which can help them improve their career path tremendously.  Just as importantly, it can help students become even more invested in what they're learning and doing.
- This could also benefit ACM and Wright State, as it could bring a lot of students together and foster a community among the CS, CEG and IT majors and others.

# The Goal
- Take the theoretical concepts taught in classes and turn them into practical projects students can apply and use *themselves, now*.
- Getting students involved in projects they can use throughout their time here at Wright State, as well as use alongside their future careers.
- Hopefully this can help build our local ACM chapter's image up and get students to join as members too.
- Homelabs are great learning environments.  By giving students the knowledge and skills needed to get started with their own homelabs, they can start learning on their own, in a safe environment.
	- Students can learn a *lot* just by being able to *break* things (safely), then trying to figure out how to fix it.

## Example Applications
> Most of the following are products I'm currently using *now*.  This means my biggest learning curve will be to translate from what I'm currently using into something I can teach to others.
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

# Proof of Concept
- I was able to quickly put together a proof-of-concept setup on campus.
	- Router: I used an old Archer C7 v2 I had laying around.  I updated it to the newest version of OpenWRT, then connected it to the campus open WiFi.  This gave any connected devices Internet access.  Note: all my devices connected with cables for this.  I could easily enable a wireless AP on the router for other devices to connect to if needed.
	- Laptop: I installed the newest version of Proxmox onto an old laptop I had laying around using a USB drive.  I also ran an `apt update` and `apt full-upgrade` on the device to confirm network functionality.  This also confirmed that I could quickly diagnose and fix the problems I ran into on-the-fly, and had a good idea of what I needed to include in my lesson plans.
	- Connected to the Proxmox web interface from another laptop.  This confirmed that the network was functional, and that I could manage the hypervisor as intended.
- Untested/unconfirmed:
	- VPN: I have yet attempt to make a VPN server inside the campus network that accepts incoming connections from outside the campus network.  This may or may not require NAT port punching, if that is even possible.
	- Peer-to-peer networking on campus WiFi: It may be possible for WiFi clients to connect to other WiFi clients on the campus network.  If this is possible, it could reduce or negate the need for our own networking devices.

# Next Steps
- Before I can schedule my first homelab workshop session, I need to finalize the following:
	1. Hardware availability.
		- Old laptops?  Not everyone will have devices they can bring.  I want to enable students to be able to learn everything, even if they won't be able to immediately apply what they learn.
		- USB drives.  We need these for installation media.
		- Monitors, keyboards, mice, power/network/video cables?  Many students might bring desktops without accessories.
		- Networking devices?  Proxmox is headless by design, and does not readily support easy wireless connectivity out the box.
		- Server availability?  I like the idea of having a common server from which I can give students access to, preferably with campus VPN support.  Not required.  This might be a side project.
	2. Networking availability.
		- I want to be able to use low cost routers with OpenWRT support to enable connectivity between devices.
		- While I have successfully connected a router to the university's wireless network without issue, I need to confirm that I'm not unintentionally or unknowingly violating some policy somewhere.
		- Test and document WiFi configuration on Proxmox in the terminal.  This is especially relevant for connecting to passwordless WiFi connections, which is not well documented.
	3. Room availability.
		- We need a room for our regular meetings.
		- Must have sufficient table space, power plugs, etc.
		- Ideally, having a room which we can store hardware in would be nice, but not required.
	4. Schedule availability.
		- I've started collecting schedule availability from those who have already expressed an interest.
		- Room availability should be confirmed with our meeting schedule.
	5. Announcements and advertising.
		- After confirming all the above, I need to have time to properly announce and advertise the workshop series.
		- This includes Jumbotron ads, Discord announcements, and possibly email and professor's plugging it in relevant classes.
		- I'm not sure how much time is *actually* required for Engage events.  As I understand it, I need to make the event on Engage, wait for approval (5 business days?) and then request a room (another 5 business days?) before I can actually announce it.  Or can I just skip most/all of that?  This makes planning and coordination very cumbersome!
	6. Planning, testing, prep work.
		- I need top put together a lesson plan of sorts.  This doesn't necessarily need to be super detailed or in-depth.  I'll likely wing a lot of this, adapting to the needs of those attending the workshops.  I want to focus on hands-on experiences, not lecture materials.
		- I need to test the hardware and software I'm going to be using.  This involves applying everything I intend to discuss in workshops before the workshop happens, giving myself time to fix any problems I might run into ahead of time.