# Getting Started Resources
===============


Before you deploy, we recommend you read Hannes’ blogs that give a good overview and starting point:

Click [here](https://www.veeam.com/blog/hardened-linux-repository-best-practices.html "Selecting Hardware and Setting Up Environment for Veeam Hardened Repository") to read the blog about the process of selecting hardware and setting up the environment for the Veeam Hardened Repository.


Click [here](https://www.veeam.com/blog/installing-ubuntu-linux-veeam-hardened-repository.html "Selecting Hardware and Setting Up Environment for Veeam Hardened Repository") to read the blog about the process of installing Ubuntu Linux for the Veeam Hardened Repository.

Click [here](https://www.veeam.com/blog/backup-repository-security-disa-stig-ubuntu-step-by-step-guide.html "Security the Veeam Hardened Repository") to read the blog post about securing the Veeam Hardened Repository.

## Ongoing Resources ##

Subscribe to and share this markdown [file resource:](https://github.com/rickvanover/VeeamHardenedRepoHub "GitHub source for this file").
 

During the VeeamON Session – we indicated that we would have an end-to-end post at the Veeam Community Hub, you can read that [here](http://vee.am/vhrhub "All-Demo Session for the Veeam Hardened Repository Playlist from VeeamON").


# Pre-Deployment Steps
===============

Much like what Hannes has in the second blog post, I recommend before Ubuntu installation ensuring the following are determined ahead of time. This way, critical questions are pre-determined before setup. 


## HWE kernel ##
During the installation - we recommend selecting the HWE Kernel, which is "hardware enablement" - this is recommended for modern server systems. If this is not visible, ensure UEFI boot mode is enabled.
![alternate text](https://img.veeam.com/blog/wp-content/uploads/2023/01/25145413/figure-01-HWE-kernel-700x488.png "HWE kernel")

## Storage Considerations ##

The VHR is going to be a large storage resource. The demos we are doing at this session are using a dedicated disk for the Veeam backups, ask yourself these questions:

* Do I want to use XFS? We recommend it. 
* What is the storage provisioned for the backups?
* How much immutability will be configured (default is 7 days)?
* What is the off-site copy -> We still recommend the 3-2-1 rule, maybe an immutable copy in object storage or another VHR in another site (completely different setup, don't do exact same setup and credentials)


## Most Critical Things to Determine Before Installation ##

1.	Networking Configuration: How many NICs, will there be bonding, what IP addressing will be used, etc.
* Subnet
* DNS
* Gateway
* IP Address(es)

2.  How disk partitioning and mountpoints will be configured; note this is much easier to do pre-installation than after installation.
3.  Much like the image above, ensure that the following information is pre-determined:
* "Your Name" for Ubuntu installation, maybe do an organization name also.
* "Your server's name" this would be the DNS name; possibly pre-create DNS if you fancy.
* "Pick a Username" this will be necessary for the Veeam Single-Use Credential, please set this name and the password and store it in a secure manner. Should you be in a test and development situation, these credentials would be needed if you were to remove the VHR from the Veeam B&R Server.

![alternate text](https://uploads-eu-west-1.insided.com/veeam-en/attachment/b8ebc505-0966-4d03-aa22-1b19f438b66a.jpg "Ubuntu Configuration")


# Post-Ubuntu Install Steps

During the session and recording, a number of steps were done post-install. The commands in Linux for change modes and set ownership are outlined in [Veeam Help Center](https://helpcenter.veeam.com/docs/backup/vsphere/hardened_repository_prepare.html?ver=120 "Veeam Help Center").

## Configuration in Veeam Backup & Replication
The steps performed are:
* Add a Linux Server
* Use the Single-Use Credential
* Ensure components install
* Add a Veeam Backup Repository
* Select type Direct Attached Storage
* Select the Hardened Repository type
* Ensure all proceeds without error

## Manage the Single-Use Credential

This will be helpful for future upgrades and updates on the Ubuntu system itself, store this in a secure manner outside of the Veeam infrastructure. Note that from V12 onward, the re-entry of the Single-Use Credential is not needed for Veeam updates (This was a common support case on upgrading from V11 to V12).

## Ubuntu Hardening ##

One of the optional, additional steps is Hardening the Linux OS. Please see this new [Veeam SYS Document](https://www.veeam.com/sys507 "Veeam Hardened Linux Repository (VeeamHub)") 

Another smart tip is ensure the networking at the switch level does not provide the VHR Linux system access to anywhere except where it needs, and no Internet access.

# Recordings of Deployment


There are a few ways you can engage in recordings of the All-Demo approach for the VHR. These are based on V12, there are some differences since V11.

## Veeam Community Hub ##

On the [page:](http://vee.am/vhrhub "Veeam Community Hub - All-Demo VHR Hub") you can replay the video I've made, it is actually hosted on YouTube but it has all of these resources. If you want to go straight to YouTube it is here:  https://youtu.be/e2SFMixp92g

This post will be visible and linked for most of 2023.

## VeeamON Portal ##

The VeeamON Portal will record the capture we did in Miami, I'll share that there are a few special Easter Eggs we did there :).

# Engage with us!

Let us know how make this better! Reach out to us for more suggestions for improvement:
Rick Vanover - rick.vanover@veeam.com  Twitter @RickVanover


