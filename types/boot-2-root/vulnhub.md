---
description: An open source repository of Boot 2 Root CTF Challenges and Write-ups
---

# Vulnhub

{% embed url="https://www.vulnhub.com/" caption="Vulnhub" %}

## Overview

Vulnhub is synonymous with Capture the Flag. For years, the website and CTF archive repository has served as a cornerstone of the community by providing a central platform to host Boot 2 Root CTF Virtual Machines. Started and maintained by an infosec legend in their own right, [g0tmi1k](https://blog.g0tmi1k.com/), the site is an open source repository of hundreds of CTF  vm's ready for download. 

## Picking a VulHub CTF

The first two considerations you should make when picking a challenge on Vulnhub are Platform and Difficulty. All VMs on the platform require either VMware or Virtual Box to run. For information on setting up a [Dedicated Virtual Machine, click the link here.](../../getting-started/choosing-your-tools/dedicated-virtual-machine/)

#### A Statement About Security 

{% hint style="warning" %}
As stated on the Vulnhub website, VMs hosted on the platform are not checked to determine if they contain malicious code. 

_"Please remember that VulnHub is a free community resource so we are unable to check the machines that are provided to us. Before you download, please read our_ [_FAQs_](https://www.vulnhub.com/faq/#security) _sections dealing with the dangers of running unknown VMs and our suggestions for_ [_"protecting yourself and your network_](https://www.vulnhub.com/faq/#protect)_. If you understand the risks, please download!" ~ vulnhub_
{% endhint %}

#### Google Dorking for Difficulty Level, VM Type, or Topic

You can use google dork queries to find CTFs based on experience level. For example, you can use the following query to find beginner level challenges

```text
site:*vulnhub.com intext:begginner
```

If you decide to use either Virtual Box or VMWare to host your CTF, you can use google dork queries to search for challenges specific to your platform. 

```http
site:*vulnhub.com intext:virtualbox
```

Likewise, you can search for specific terms. For example, if your interested in OSCP-like CTF's, you can use the command intext:OSCP. 

```http
site:*vulnhub.com intext:OSCP
```

#### Searching Through Upload History

To see all CTF's hosted on Vulnhub, you can browse the timeline page.

{% embed url="https://www.vulnhub.com/timeline/" caption="Link to the VulnHub Timeline" %}

## Downloading the CTF VM

This step will differ depending on your chosen Virtualization Software. If you have not already installed VMware or Virtual-box, [click here for instructions on setting up your host workstation. ](../../getting-started/choosing-your-tools/dedicated-virtual-machine/)The steps below are written for Mac OSX, but should be very similar for windows and other host operating systems. 

{% hint style="success" %}
Vulnhub CTF Installation Tutorial : [Raven CTF](https://www.vulnhub.com/entry/raven-1,256/)
{% endhint %}

### VMWare

This tutorial will be based on the [Raven CTF](https://www.vulnhub.com/entry/raven-1,256/), but will be the same across challenges. On the main vulnhub page for your chosen CTF, locate the Download section and download the CTF with extension\*.OVA.  Some CTFs can be larger in size, most are typically within the .5 - 1.5 GB range. 

![](../../.gitbook/assets/screen-shot-2020-06-15-at-12.28.17-pm.png)

Once the ova images is downloaded it, is is suggested to move to a dedicated folder for vm's. For example Documents/CTF/VMs. At this point, you can right click the image, and select "Open with VMWare"

![](../../.gitbook/assets/screen-shot-2020-06-15-at-12.42.07-pm.png)

Select Continue. VMWare will save the file with the \*vmwarevm extension. Select Finish

![](../../.gitbook/assets/screen-shot-2020-06-15-at-12.43.43-pm.png)

On the main menu for VMWare, you should be able to see the new CTF as a VM. You can group VMs together according to category and put them in corresponding folders like CTFs and Attack Machines. Changing a VM folder here will not change the actual location of the image on your system. 

![Organizing your local workspace by category](../../.gitbook/assets/screen-shot-2020-06-15-at-12.45.57-pm.png)

{% hint style="danger" %}
Before launching a challenge VM, it is important to ensure the networking settings are only enabled for your local machine. This is a safety precaution you can take to ensure that no malicious code can connect to the outside internet 
{% endhint %}

To set network settings, right click the VM and select Settings.

![The settings menu in VMWare](../../.gitbook/assets/screen-shot-2020-06-15-at-1.48.27-pm.png)

In the settings menu, navigate to Network Adaptor. Select the "Private to my Mac" setting. Your VM will now only be accessible to other machines that are "local to your mac" and not accessible by the wider internet. 

![](../../.gitbook/assets/screen-shot-2020-06-15-at-1.45.57-pm.png)



## Configuring DCHP

In order to connect your attack virtual machine to the same local network that the CTF Challenge is on, you need to ensure DCHP is enabled and working properly. Dynamic Host Configuration Protocol \(DHCP\) is a  protocol which assigns machines on a network with an IP address, an essential function of networking. Luckily, many Vulnhub challenges come pre-configured with DCHP enabled. If configured correctly, all you need to do is ensure your attack platform and your target machine  both have network adaptors set to host-only. 

_Read more about DCHP Here_

{% embed url="https://docs.microsoft.com/en-us/windows-server/networking/technologies/dhcp/dhcp-top" %}



## Getting Started

Start both your target machine and your attack platform by right clicking, and selecting "Start Up" from the drop down options. This is the last interactive step you will do on the target machine through your virtualization software. At this point, the CTF challenge has begun. 

![Starting the Raven CTF VM](../../.gitbook/assets/screen-shot-2020-06-15-at-1.48.21-pm.png)

### Check for a connection

Before testing the target for vulnerabilities, you will need to confirm it is connected to the network. There are several ways to do this.

#### Ifconfig 

Use the linux networking utility ifconfig to check network connections 

```bash
ifconfig 
```

#### Arp-Scan

Use arp-scan to listen for other hosts on the network sending ARP packets

```bash
arp-scan -I [interface] -l
```

#### Netdiscover

Use netdiscover to find other hosts on the network

```bash
netdiscover -i [interface]
```

#### Nmap Ping-Sweep

Use nmap to sweep the network for live hosts

```bash
nmap  -sP [CIDR Range]
```

## Cleaning Up

When it is time to stop the challenge for any extended period of time, you should always shut down both the target and attack VM. Leaving these running in the background will significantly reduce your host computers resources and can cause slow performance and overheating.

## Submitting a CTF to Vulnhub

## 

