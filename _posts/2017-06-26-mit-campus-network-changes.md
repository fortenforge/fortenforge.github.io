---
layout: post
title:  "A guide to MIT's campus network changes for the non-expert"
date:   2017-06-26 3:12:44 -0500
categories: misc
use_math: true
---

There's been a lot of buzz on dorm mailing lists and [online forums](https://news.ycombinator.com/item?id=14637850) about the changes that [IS&T](https://ist.mit.edu/) is making to MIT's campus network. This post attempts to break down and explain the changes to a non-expert in networking in order to clear up some of the confusion surrounding the discussion.

First, a brief introduction to IP addresses and Network Address Translation (NAT):

<!--more-->

# IP Addresses
Every computer connected to the Internet has an associated IP address that serves to identify and locate it in the network. Suppose that your computer has IP address 18.9.64.26 and wants to talk to Google, with IP address 172.217.6.46. It does so by initiating a TCP request and sending a packet with *destination* 172.217.6.46 and *source* 18.9.64.26. When Google replies to your request, it sends a packet with destination 18.9.64.26 and source 172.217.6.46. Most of stuff that goes into making the Internet work involves making sure that a packet destined for a particular IP address eventually reaches its destination.

In IPv4 (the version currently supported and used by the entire Internet), IP addresses take the form of 32-bit numbers represented using [dot-decimal notation](https://en.wikipedia.org/wiki/Dot-decimal_notation)—basically, IPv4 addresses look like `a.b.c.d` where `a`, `b`, `c` and `d` can range between 0 and 255 inclusive. In the early days of the Internet, the IPv4 space was sliced up and allocated to various corporations and entities; MIT actually received all the IP addresses that start with 18 (more on this later).

# NAT
Various estimates put the number of Internet-connected computers somewhere in the range of 6-12 billion. Given that there are only \\(256^4 = 2^{32} \approx 4\\) billion different IPs in IPv4, we seem to have a [problem](https://en.wikipedia.org/wiki/IPv4_address_exhaustion). The long-term solution is [IPv6](https://en.wikipedia.org/wiki/IPv6) which increases the IP address space to \\(2^{128} \approx 3.4 \cdot 10^{38}\\). However, IPv6 deployment has been slow-going (more on this later too), so a number of more short-term fixes have been adopted in the meantime.

The most popular fix is a technique called Network Address Translation, or NAT. Here's how it works:

First, a portion of the IPv4 space was [reallocated](https://tools.ietf.org/html/rfc1918) for use by *private networks* (home, office or enterprise environments). These IP addresses can be used by anyone for free without approval from any governing body, but they are not publicly accessible (because they're not unique to each computer). For example, any IP address that begins with "192.168" is one of these so-called private IP addresses. My computer's IP address is 192.168.4.6, but outside of my home's local network, I can't expect to address a packet to 192.168.4.2 and have it delivered to it.

So, how does my computer talk to Google? Well, first it sends a packet with source 192.168.4.6 and destination 172.217.6.46 to my home router, which *does* have a public IP address of 184.23.225.146. The router then modifies the source address of the packet to 184.23.225.146 and sends it out to Google. Google then replies with a packet with source 172.217.6.46 and destination 184.23.225.146 which comes back to my router. The router then modifies the destination address of the packet to 192.168.4.2 and sends it to my computer.

There are more problems to solve (how does the router know whether to send a response from Google to my computer or my phone?) but that's how NAT works at a high level. NAT allows an entire private network to masquerade behind a single public IP address, and it's been one of the key adoptions that has allowed the Internet to grow to billions of devices without running out of IP addresses.

It also comes with a nice side-benefit: suppose that I have a computer at home that is running an SSH server. If my computer's IP address is public, anyone in the world who knows its IP address can try to guess my username and password and login remotely. However, if it's on a private network with NAT, only other users on the network can SSH into it, but it can still talk to and access the broader Internet. So, while NAT wasn't designed as a security measure, it can provide a security advantage.

# MIT's Network
The early Internet was formed mostly by joining together several university networks. MIT was one of these founding networks, so when it came time to dividing up the IPv4 space, MIT was allocated a hefty chunk of IP addresses, specifically the "18.0.0.0/8" block, which meant that any IP address beginning with 18 was owned by MIT. This includes \\(256^3 \approx 17\\) billion addresses and is a full \\( 1/256 \\) of the total number of IPv4 addresses. This is a massive number and enough to give 700 different IPs to each student or employee of the university.

Given this surfeit of addresses, MIT's network never bothered with NAT: any computer that joined the network was assigned a public IP in the block. This meant that if a student wanted to run a server out of his or her dorm room it was as easy as finding a spare computer, connecting it to the network, and running the server. Obtaining a *static* IP that didn't change after a reconnection to the network was as easy as [filling out a form](http://rcc.mit.edu/ip-request). Students took advantage of this to build and maintain websites, databases, and music servers.

In late April of this year, students received an email from MIT's Provost, informing them that MIT would ramp up efforts to transition to IPv6 and sell some of the excess IPv4 addresses and use the money to "support activities focused on the future of the Internet and the global cyber-infrastructure". Some students lamented the loss of the iconic 18.0.0.0/8 block, but the move did not attract that much controversy.

Then, on June 23rd, a student found [an internal IS&T presentation](/assets/mitnet/mitnet.pdf) that announced a planned transition to a private, NAT'ed network. Under the new scheme, devices would be assigned an address in the 10.0.0.0/8 block (reserved for private networks) and would not be publicly accessible. This move would have enormous consequences on the student- or community-run servers that had been built up over the years.

Even more disconcerting was the realization that this process was *already underway*. [WMBR](wmbr.mit.edu)'s [track-blaster](http://track-blaster.com/) service was the first student-run server to fall victim to the transition, and was briefly inaccessible from the public Internet for a period of time. In response, it looks like IS&T set up a public network for building 50 with 256 IP addresses and assigned track-blaster a public IP from that pool. As of now, it's unclear whether such a network will be setup for any other buildings.

IS&T could certainly have done a much better job of informing and working with the MIT community to make the transition cleaner. The internal presentation says:

> As this is a significant migration effort for the campus, we will be providing
resources and services through our DITR team to assist members of the MIT
community throughout the transition

but as of yet, no resources have emerged. The presentation also promisingly claims that "Provisions will be available to provide for a public IPv4 address should it be required." Again, as of yet no details on these provisions have emerged.

# Advantages

So, why would IS&T want NAT in the first place? Even after the sale, MIT still has enough IPs to continue assigning public addresses to each device. One reason might be the security advantage provided by a private IP.

Before, MIT was constantly getting bombarded with port scans and SSH attempts from script-kiddies looking to add a vulnerable server to their botnet. Indeed, I know of at least a couple incidents where a student set up a raspberry pi with the default username and password and the device quickly became infected and started port-scanning (looking for other devices to pivot towards). A private network mitigates a lot of these concerns simply by making the default state of any computer to be not accessible from outside MIT.

There might be another reason to transition to NAT: maybe MIT wants to sell even more of their IPv4 addresses. The IS&T presentation talks about MIT's transition to IPv6 (where, once again, MIT has secured an enormous chunk of IP addresses). If in the long term, MIT envisions its network as being mostly IPv6, it has little need to use the remaining IPv4 addresses. NAT allows MIT to slowly sell off an increasing number of IPv4 addresses without ever being concerned about address exhaustion during the IPv6 transition.

Each IP currently sells for about $10; MIT's current sale netted it a cool $200 million. Perhaps MIT wants to get rid of most of their IPv4 space before IPv6 becomes widespread and the price for IPv4 IPs plummets.

# Going forward

Clearly, IS&T should have done a much better job articulating their motivations and plans for the transition. I hope that before they proceed with the NAT implementation, they clearly outline the provisions and resources that will be put in place so that students can continue hacking away in their dorm rooms.
