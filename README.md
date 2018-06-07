# raspberry-pi
UBports Raspberry Pi Focus Group. Join the discussion on [our forum](https://forums.ubports.com/category/43/ut-for-raspberry-pi) and our [Telegram focus group](https://t.me/UBports_pi).

## Contents
1. [Goals](#goals)
2. [Benfits](#benefits)
3. [Conceptional Questions](#conceptional-questions)
4. [FAQ](#faq)
5. [Team](#team)

## Goals
### Desktop
* Have Ubuntu 16.04 with Unity8 running on a Raspberry Pi
* Provide easy install method (usally by providing an ready-to-use image)
### Phone
* Have Ubuntu Touch running on a Raspberry Pi with at least a Touch Screen
* Enable the use of additional phone hardware (TouchScreen, Battery, Modem, other
Sensors)
* Make every UT core app/component and OpenStore work on a Raspberry Pi
* Provide an easy install method
* Provide updates

## Benefits
* Non-Android-Architecture
  * Synergy effect with Librem 5 (booting and updates without fastboot/recovery)
  * Possible Standardization of Android-Free-UT, like Rootfs could become a blueprint for
Non-Android-Phones
* Development board for Ubuntu Touch
  * Enables enthusiasts to build there own phones with Ubuntu Touch (these people are in
the telegram group already)
  * Enables App developers to develop on a real arm Ubuntu Touch device
* Unity8 desktop side
  * Developing and testing towards convergence (HDMI, USB, Bluetooth)
* Community
  * The Raspberry Pi community is huge and full of enthusiasts
  * The UBports Raspberry Pi project could attract developers and power users to Ubuntu
Touch
  * Raspberry is widely used in education, there could be cooperations with initiatives, e.g.
where students learn what a smartphone consists of or even build there own phones

## Conceptional questions
* How to boot Ubuntu Touch on a non-Android-Device?
* How to install OTA-Updates on a non-Android-Device?
* How to enable the use of different hardware?
* Partition layout?
* What are exact differences between Ubuntu and Ubuntu Touch? Which are just needed for
Android-devices and which are by design?
* What needs to be adapted in Ubuntu Touch to make it work with a Raspberry Pi?
* How to handle the different Raspberry Pi Models?
* How does the variable size of SD cards in a Raspberry Pi affect installation and update
concept?
* How does the architecture aarch64 us? 

## FAQ
### Why don't you use Android?
Short answer: because its a pain and ugly, should ba avoided and we don't need it on the RaspberryPi. ;-)
Long answer: What is the Android layer used by Ubuntu Touch? It's an extremely minimal Android container, which ideally contains only the bits providing hardware enablement (kernel with driver modules, and nothing such as GUIs, app runtimes and libraries...).
This function (hardware enablement, that is the ability of the operating system to detect and use the hardware) is provided ususally by the mainline Linux kernel (on desktop computers, laptops, servers...). But in the case of Android devices, the mainline kernel usually doesn't have the hardware enablement features for the device, so we are forced to use the kernel of the Android image, which has been adapted by the vendors to work on the device. But even using the Android kernel instead of the mainline kernel is not enough, since some driver modules are not in the kernel, but in the Android userspace (e.g. GPU, camera), the so-called *blobs*; since they are not part of the kernel they can be closed-sourced.
It's for this reason that we create a very minimal Android container, just to get hardware enablement with the kernel and the blobs, but ideally nothing more. I say ideally because being Android build process so complex, something unneeded may slip in the container anyway.
So, in the case of the RaspberryPi, the Lineage project has probably just taken some version of the mainline kernel (which already has support for RaspberryPi), and built Android over it. If we use Lineage to port Ubuntu Touch to the RaspberryPi, we are just putting the mainline kernel, maybe modified to run Android and maybe not updated as it should, and Android stuff that we don't need between us and the hardware while we can just use the mainline kernel as any normal computer.

## Team
* @jonny aka Jonatan Hatakeyama Zeidler (Moderator, Developer)
* @Stereofont aka Lionelb (Moderator)
* @Stason888 aka Seven (Moderator, Developer, is already building his own Raspy-Phone)
* Many members in the telegram focus group
  * many of them seem to have Raspberry Pis
  * some already share ideas on the concept
  * we have no idea yet, who is going to really contribute
