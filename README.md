# WiVRn: A Comprehensive Wireless VR Guide

**_Please carefully read everything, especially the [requirements](#requirements) and [compromises](#compromises) sections, it will save you a lot of headaches and frustration._**

**_Please also note this guide is based upon my own experiences, testing, and opinions and is by no means a comprehensive guide to everything VR or Linux!!! I am simply sharing my advice based on my own testing!!!_**

---

## Summary

The best way I have found to play with standalone VR headsets in Linux is by using [WiVRn](https://github.com/WiVRn/WiVRn).

WiVRn is a solution similar to [ALVR](https://github.com/alvr-org/ALVR), [Air Link](https://www.meta.com/help/quest/509273027107091/), and [Virtual Desktop Standalone](https://www.meta.com/experiences/virtual-desktop/2017050365004772/), all providing a wireless solution to VR gaming. ALVR supports both Microsoft Windows and Linux, while both Air Link and Virtual Desktop Standalone both only support Microsoft Windows.

WiVRn supports both wired (via USB) and fully wireless play, but this guide only covers wireless VR, as I personally have not tried a Link Cable before.

I fully consider standalone wireless VR as fully stable for regular everyday use, assuming all of the following requirements are met.

## Requirements

- **Basic knowledge of Linux and terminal/command line.**
  
  - Not everything can be done with a GUI, and some terminal usage will be needed
  - Basic knowledge of terminal and how to solve issues yourself will go a long way, especially if something goes wrong.
  - Ability to search for help and answers on your own via Google/Reddit.
  - Understanding the importance of finding and following relevant documentation.
- **A headset that is supported by WiVRn.**
  
  - WiVRn supports the following headsets for wireless play:
    - Quest 2, Quest 3, Quest 3S, Quest Pro, Pico Neo 4, HTC Vive Focus 3, and HTC Vive XR Elite
- **A decent WiFi 5 or newer (AC, AX) network.**
  
  - WiVRn requires a decent wireless and wired network with little to no interference. I have tested WiVRn on both AC and AX networks. I highly recommend a dedicated router in AP (access point) mode directly connected to your computer via wired ethernet to greatly improve the experience.
    - _There is a wired USB mode for WiVRn, but I have not tested it myself, so it is not covered by this guide._
- **Wired Gigabit connection between computer and router.**
  
  - Latency and quality will both have issues if you try using any form of wireless/hotspot to connect your computer to your router. Other solutions like Air Link, ALVR, and Virtual Desktop also **REQUIRE** a wired GIGABIT connection from the computer to the router, and so does this guide. ***YOU MUST HAVE WIRED ETHERNET FROM YOUR COMPUTER TO YOUR ROUTER!!!*** Use of wireless hotspots is NOT SUPPORTED under any circumstances.
- **A stable network.**
  
  - A correctly configured ethernet and WiFI network, as well as no wireless interference is essential for a good wireless VR experience. See the [Advanced Network Testing](#Advanced Network Testing) subsection in the Troubleshooting section for information on how to fully test your local network.
    
    - NOTE: Your internet speed DOES NOT matter for wireless VR -- but your LAN speed does! This includes both your wired and wireless network, as well as your networking card and cables. All of these things need to be working correctly.
      

- **Linux kernel version 6.15 or newer.**
  
  - [ntsync](https://docs.kernel.org/userspace-api/ntsync.html) requires newer kernels. Without it you may run into performance degradation, graphical glitches, or crashes, and some games will not work correctly at all (such as [VTOL VR](https://store.steampowered.com/app/667970/VTOL_VR/))
- **A proton branch that supports [ntsync](https://docs.kernel.org/userspace-api/ntsync.html), such as [Proton-GE](https://github.com/GloriousEggroll/proton-ge-custom) or [cachyos-proton](https://wiki.cachyos.org/configuration/gaming/#essential-packages).**
  
- **Stable hardware, software, and network.** Many VR issues can be tracked down to being unrelated to the VR hardware or software. Ensure your system is up to snuff before attempting to run VR in Linux.
  
- A fully functioning [Steam](https://store.steampowered.com/about/) installation.
  

## Compromises

WiVRn has several limitations compared to other streaming solutions, especially those that utilize Microsoft Windows. Before deciding if this guide is for you, be aware of the following limitations:

- **No spacewarp/motion smoothing.**
  
  - Currently no form exists for Linux that I personally know of. If you run older/weaker hardware and are already heavily dependent on frame gen to provide stable frame rates in VR, be aware that your FPS will be cut in HALF by moving to Linux due to lack of any motion smoothing. You can compensate by lowering your streaming resolution, but it will result in a loss of quality otherwise.
- **Time investment:**
  
  - Expect some extra troubleshooting and setup, as per this guide. Knowledge is key, and although the switch from Windows to Linux seems daunting, it just takes learning and practice like with anything. This guide should help you on your journey, and make things far more painless for you.

---

## Tested Linux Distributions

*NOTE: this section is based on my own recommendations, experiences, and testing. There are as many Linux distributions as stars in the night sky, so this is not a comprehensive list.*

I have personally tested VR in both [Bazzite](https://bazzite.gg/), [CachyOS](https://wiki.cachyos.org/cachyos_basic/why_cachyos/) and [PikaOS](https://wiki.pika-os.com/en/home).

### Bazzite

[Bazzite](https://bazzite.gg/) is an semi-immutable distro by [universal blue](https://universal-blue.org/) based on [Fedora Atomic](https://fedoraproject.org/atomic-desktops/). A highly simplified distro, it is mainly designed for ease of use and is very beginner friendly. Mainly uses [Flatpak](https://flatpak.org/) for applications which can easily be installed via the [Bazaar](https://github.com/kolunmi/bazaar) app store. The system is much more locked down that traditional distros, and it is mainly geared towards HTPC setups with controllers. Also has builds for handhelds like the SteamDeck. *NOTE: I personally use Bazzite on my desktop as my main operating system, and I have been using Linux since 2006 (Debian Sarge).*

### CachyOS

[CachyOS](https://wiki.cachyos.org/cachyos_basic/why_cachyos/) is a traditional rolling release distribution based on [Arch Linux](https://archlinux.org/). CachyOS has gained a lot of momentum the past year, and recently reached #1 most popular distro on [Distrowatch](https://distrowatch.org). Features the complexity and flexibility that Arch offers, but simplifies a lot of the setup and comes with tons of tweaks specific to newer hardware, as well as a great GUI installer. Features x86_64-v3 optimized packages for newer CPUs as optional choice during installation. *NOTE: CachyOS is the best "traditional" Linux distro I can recommend to users both new and old.*

### PikaOS

[PikaOS](https://wiki.pika-os.com/en/home) is a fairly new rolling release distro based on [Debian](https://www.debian.org/intro/why_debian). Unlike Bazzite, PikaOS is a traditional distro that doesn't lock down the system. Features tons of gaming related tweaks like CachyOS, but requires more modern CPUs that support x86_64-v3. A stable base with updated applications thanks to custom packages and Flatpaks, PikaOS uses [Discover](https://apps.kde.org/discover/) as it's app store. Similar to Bazaar that Bazzite uses, Discover is much more mature and features full category sorting. *NOTE: PikaOS is a newer distro that hasn't matured as much as the others. It also features an older kernel and modules, and may cause issues. For me, I had repeated USB resets with my 10 port powered USB hub, even though no other distros had this issue.*

## Choosing a Distribution

My recommendation for a distro is very simplified, but should get you setup on the right track.

### Bazzite

Bazzite is best served as a HTPC hooked up to a large TV. Bazzite can auto-start inside of Steam Home, giving the Steam PC experience on large screens. It's desktop experience is very good though, and fully usable on desktops as an everyday operating systems. Bazzite has SELinux enabled by default, and it also fully supports Secure Boot and TPM auto-unlock for LUKS encrypted root volumes.

### CachyOS

CachyOS is hailed for it's flexibility, speed, and availability of most software due to the [Arch User Repository](https://aur.archlinux.org/). CachyOS is also a traditional distro that uses native packages. I wouldn't recommend CachyOS to novice computer users. Expect things to work out of the box, but if you want to tweak it you need to learn to ready CachyOS and ArchWiki documentation in detail or you will run into issues.

The AUR also can be very dangerous if you do not fully check and understand PKGBUILDs -- recently malware was discovered on the AUR that many users installed. Recently the AUR has come under DDOS attacks, which can completely cause clean installs to fail.

Check the [Arch Linux Status](https://status.archlinux.org) page for information on the mirror status before attempting to install CachyOS or you can run into the "failed to run chwd" error message during installation due to certain packages being unavailable for installation or update.

### PikaOS

PikaOS is still a very new distro without a well known proven track record, but is still ready for daily use. Very beginner friendly like Bazzite, but features similar performance and tweaks like CachyOS, this is a very good distro. This is a good choice if you are familiar with Debian and prefer having a very stable base. Note that because it is based on Debian, certain packages related to your desktop environment will be slightly more out of date compared to the other distros.

## WiVRn

[WiVRn](https://github.com/WiVRn/WiVRn) wirelessly connects a standalone VR headset to a Linux computer. You can then play PCVR games on the headset while processing is done on the computer.

### WiVRn Installation

The installation method for WiVRn will vary depending on your distro of choice.

#### Bazzite/PikaOS

Search for "WiVRn" in your package manager of choice (Bazaar on Bazzite or Discover and PikaOS) and install the Flatpak for it.

![Bazaar Flatpak Manager](/assets/images/bazaar_wivrn.webp?msec=1757257046966)

#### CachyOS

If you are on CachyOS, you can use the following command to use paru to install it from [Arch User Repository](https://aur.archlinux.org/packages/wivrn-dashboard):

> `paru -S wivrn-dashboard`

## WiVRn Setup

Go ahead and launch WiVRn via your application launcher if you have not already.

You will first be greeted by the setup wizard. For this guide, you can skip the wizard completely by clicking through it and accepting all defaults until you get to the main page:

![WiVRn Dashboard](/assets/images/wivrn_dashboard.webp?msec=1757257046966)

Note the two sliders:

- Running:
  
  - If this is toggled off, WiVRn will not run or accept connections from any headsets. You should always leave this toggled on.
    - _Note: The WiVRn dashboard **MUST** be open on your desktop or the server will not be running or accept new connections. Completely closing the WiVRn dashboard completely shuts it down entirely._
- Pairing:
  
  - Enabled by default, the pairing slider allows headsets to be paired to your computer.

First, let’s set up WiVRn optimally for streaming quality and performance. Go ahead and click the “Settings” button in the top right of the WiVRn dashboard.

![WiVRn Dashboard Settings](/assets/images/wivrn_dashboard_settings.webp?msec=1757257046966)

Edit the following settings:

- Manual foveation:
  
  - Set this to a minimum of 20%. Setting it lower than 20% may result in encoder overload in Linux. You can increase the slider to higher values to decrease encoder load, but the higher you go the more the outside of the image in your headset will be rendered at a lower resolution, reducing image quality the higher you go. 20% appears to be the sweet spot for Quest headsets.
- Bitrate:
  
  - This setting will depend on your encoder, available GPU power, and your wireless network. A good starting point is the default 50 MBit/s, which any decent router and network setup can easily handle. I personally use 120 MBit/s, as that is a decent balance of latency and quality.
    - _NOTE: Values higher than 120 MBit/s may result in encoder or network overload depending on your hardware setup._
    - _NOTE: Close the app on your headset, fully shut down your VR game, and fully restart the dashboard to ensure the settings take full effect after making any changes._
- Encoder Layout:
  
  - To set up the encoder layout, use the drop down box and select the “Low latency preset”. This will split the encoder into three threads, and you can then click in each box and force each of them to vaapi with H.265. Make sure not to click the center of the boxes or it will create another encoder split and you will have to start over.

Refer to the following tables to determine what encoder and codec to use. Take note that your hardware must also support the relevant codecs to be able to use them.

- Quest 2 | Quest Pro | Pico Neo 4 | HTC Vive Focus 3 | HTC Vive XR Elite:

| GPU | Encoder | Codec |
| --- | --- | --- |
| AMD | vaapi | H265 |
| NVIDIA | nvenc | H265 |

- Quest 3, Quest 3S

| GPU | Encoder | Codec |
| --- | --- | --- |
| AMD | vaapi | AV1 |
| NVIDIA | nvenc | AV1 |

If your GPU hardware doesn't support AV1, use H265 as fallback instead.

You can try switching your codec to h.264 to get a reduction in latency, but note that you may see more banding in gradients if you do so. (This is true even on 8 bit displays!)

---

## WiVRn App

For Meta Quest headsets, simply install the WiVRn app from the Meta Quest store on your headset.

For others, you must download the APK and sideload it manually. The latest APK can be found on the [GitHub](https://github.com/WiVRn/WiVRn/releases) releases page for WiVRn.

### WiVRn App Setup

Once the app is installed, open it on your headset. You will be greeted by a simple UI. By default, camera passthrough will be enabled on headsets that support it.

Go ahead and click on your computer using the green “Connect” button. Make sure that the dashboard is open and running on your computer, and that your headset is connected to the same network.

You need to enter your pin PIN listed on the WiVRn dashboard the first time you connect to verify the connection.

Sometimes the code will time out as pairing mode disables after a few minutes for security. Move the pairing slider in WiVRn over to the right by clicking on it to re-enable pairing, or fully restart WiVRn on your computer and try again.

Please also note that your firewall may block connections to your PC. Refer to the [WiVRn GitHub page](https://github.com/WiVRn/WiVRn?tab=readme-ov-file#my-headset-does-not-connect-to-my-computer) for instructions on what ports to allow.

![WiVRn Headset Server List](/assets/images/wivrn_headset_server_list.webp?msec=1757257046966)

Once connected to your computer, you should see a message stating it was successful like so:

![WiVRn Headset Connected Message](/assets/images/wivrn_headset_connected.webp?msec=1757257046967)

At this point, WiVRn is connected to your computer and is waiting for a game to start. By default, there is no way to control your Linux desktop or launch games from within the headset itself, but we will address this shortcoming later in the guide.

Now click the blue “disconnect” button as we need to change some settings in the app directly for the best experience.

### WiVRn App Settings Tab

Select the settings page on the left side of the panel in front of you.

![WiVRn Headset Settings Tab](/assets/images/wivrn_headset_settings.webp?msec=1757257046967)

- Refresh Rate:
  
  - I recommend only using at max the 90 Hz refresh rate on battery powered headsets. 120 Hz will heat up your headset SOC and battery, and decrease your overall internal battery lifespan vs 90 Hz, as well as reduce battery life by around 25%.
- Resolution scale:
  
  - By default, WiVRn runs games at 140% resolution.
    - The extra 40% accounts for [barrel distortion](https://developers.meta.com/horizon/documentation/native/pc/dg-render/). Note that this article applies to all modern headsets, not just Rift as the documents suggests.
    - If you have a weaker GPU, you can turn this slider down to improve performance, which will result in a loss of image clarity. Note that turning the slider down will decrease the resolution and clarity in the center of the display first -- the lower the resolution slider is, the bigger the circle with a lower resolution will become.
- Enable microphone:
  
  - Enable this to allow the in-headset microphone to pass through to your computer. You will get a prompt from the headset asking to enable microphone permissions, and you must accept them for microphone passthrough to work.
- Show performance metrics:
  
  - Enable performance metrics which will show an overlay when you connect to games to troubleshoot performance (this overlay will show up by default and can be hidden by pushing both thumb sticks down at the same time). The overlay is a great troubleshooting tool.

### WiVRn App Post Processing Tab

![WiVRn Headset Post Processing Tab](/assets/images/wivrn_headset_post_processing.webp?msec=1757257046967)

Enable quality sharpening when running the default 140% resolution. If you turn the slider down, you would turn sharpening off and use quality supersampling instead.

Snapdragon Super Resolution has been replaced by the OpenXR processing options at the top, which you can see the warnings about by hovering over the yellow warning icon in the app.

---

## Valve Proton

The recommended proton version will vary depending on your distro of choice, and also on the specific game you want to play.

There are many resources you can use to check game compatibility and determine the best Proton version to use for a specific game or distro.

- [ProtonDB](http://protondb.com/)
  
  ProtonDB is a crowd sourced compatibility list for games on Proton in Linux. You can simply search for your game on the site. Use the filter options on the site to search for similar hardware specs to yours, and even sort reports by distro. A great resource for determining relevant Proton versions or launch parameters needed to get your games working. You can also easily submit your own reports to help out the community!
  
- [Are We Anti-Cheat Yet?](https://areweanticheatyet.com/)
  
  A great resource for checking if your online/multiplayer game supports Linux. Certain games, particularly those with kernel level anti-cheat don't support Linux and may even ban you for attempting to play. Note that using kernel level anti-cheat even in Microsoft Windows can have various [possible privacy, security, stability, and performance drawbacks](https://gist.github.com/stdNullPtr/2998eacb71ae925515360410af6f0a32#the-risks-of-kernel-level-access), and it's highly unlikely such level of access will ever be adopted into Linux because of these issues due to the ethical and security concerns of such wide access.
  

### Bazzite/PikaOS

- [Proton-GE](https://github.com/GloriousEggroll/proton-ge-custom)Proton-GE is a very popular version of Proton that is not associated with Valve or Steam. Created and maintained by Thomas Crider, aka [GloriousEggroll](https://github.com/GloriousEggroll), this version has lots of tweaks and improvements over the default proton versions, and also has ntsync support enabled in it's latest versions.
  - Install: Open up ProtonPlus from your application launcher (installed by default).

![ProtonPlus](/assets/images/ProtonPlus_Main.webp?msec=1757257046967)

Click on “Proton-GE” listed at the top of the page in ProtonPlus.

![ProtonPlus ProtonGE](/assets/images/ProtonPlus_ProtonGE.webp?msec=1757257046967)

Click on the download icon next to "Proton-GE Latest" and wait for it to download. If you run into issues with games on this latest version, try the next one down on the list (GE-Proton10-10 in the example image).

There are tons of other Proton versions you can try, but I personally have never needed to use any others. Some work better on much older GPUs or help for running much older games.

### CachyOS

There are two custom proton versions that come bundled with CachyOS.

- **proton-cachyos** - based on Proton bleeding-edge, this is a custom Proton version that uses native libraries and has a ton of tweaks. This is best installed along with Steam and other dependencies using the [CachyOS Wiki](https://wiki.cachyos.org/configuration/gaming/#essential-packages) instructions.
  
- **proton-cachyos-slr** - a version of Proton that supports both [Easy Anti-Cheat (EAC)](https://www.easy.ac/) and [BattlEye (BE)](https://www.battleye.com/) anti-cheats in games. If a game you play uses either of these, make sure to install the package "proton-cachyos-slr" and manually enable it for each game that needs it. Without this proton version you risk being kicked from servers or having connection issues.
  

You can easily install both of these versions of Proton in CachyOS with the following command:

> paru -S cachyos-gaming-meta proton-cachyos-slr

This has the advantage of integrating updates to these Proton versions with your regular system updates, simplifying upgrades.

In addition to these CachyOS specific versions, you can also easily install ProtonPlus and also use Proton-GE if that version gives you better supports for certain games.

## Enabling ntsync

To enable ntsync, you must manually enable it for each game that you want to use it with. This must be done on a per-game basis in each individual games properties in Steam.

![Steam Launch Parameters](/assets/images/steam_proton.webp?msec=1757257046967)

### Verify ntsync is functioning correctly

To check if ntsync is working, simply launch a game once the launch parameter has been entered and use lsof from the terminal:

> lsof /dev/ntsync

This will print out any processes using ntsync at the time of running. It should list various steam processes, including your game executable.

Note that this only means ntsync is enabled with your game. Most games will work fine with ntsync and may receive various performance benefits that come with it, but for some games it may cause issues. Perform your own testing to determine if it is worth using, especially if the game isn't covered in

---

## WiVRn Connection

Now, go ahead and reconnect WiVRn to your computer. It should say connected and is now waiting for you to start a game.

## Select Audio Devices

By default, WiVRn will configure the streaming audio devices on your computer, but both the output and input audio streams for WiVRn should be selected by you on your desktop.

You can do this by left clicking on the audio icon in your tray and selecting WiVRn as both default output and input devices while connected.

These should auto connect in the future when you connect, and only need to be selected the first time. The output will send your audio from your computer to your headset, and the input will send the Quest headset's microphone back to your computer for the game to use.

If you use a different audio device like a separate headset, just select those audio devices instead.

## Testing a game

At this point, it is a good idea to just launch a VR game and see how the it runs before playing with mods. You will have to manually run the game from Steam on you monitor the first time.

If the game starts on your desktop but doesn’t connect to the headset, try fully re-booting WiVRn and Steam. Sometimes it also takes a full reboot of the headset and computer to make things work.

You way tweak the WiVRn dashboard settings as discussed previously. Try increasing or lowering the bitrate as needed.

If you still have quality or stream corruption issues, especially if having to drop the bitrate down to 50 MBit/s or lower, then suspect a faulty hardware or software install, or network quality issues.

---

## wlx-overlay-s:

[wlx-overlay-s](https://github.com/galister/wlx-overlay-s) is a VR overlay for Linux that allows you to fully control your desktop from within VR, similar to how overlays such as xsoverlay or OVR Toolkit work in SteamVR on Windows.

You will be able to fully control your PC monitors, type on a virtual keyboard, listen to music, watch videos, and use your web browser in your headset.

![wlxoverlays](/assets/images/wlx-s.webp?msec=1757257046967)

### wlx-overlay-s Install

Installing wlx-overlay-s will vary depending on your distro of choice.

#### Bazzite/PikaOS

The easiest way to get wlx-overlay-s is to use it's Appimage release provided on it's GitHub page.

Go to the [GitHub](https://github.com/galister/wlx-overlay-s/releases) page and download the latest AppImage from the releases page.

Then open your relevant app store (Bazaar on Bazzite and Discover on CachyOS/PikaOS) and search for "Gear Lever" and install it. We will use it to install and manage AppImages on your system.

Once downloaded, right click on the Appimage file on your computer and select “Open with Gear Lever”.

![Open with "Gear Lever"](/assets/images/gear_lever.webp?msec=1757257046968)

You must click “unlock” to verify you want to make changes in Gear Lever, then you can click “Move to the app menu” to install the Appimage on your system. The image will be moved into the folder “AppImages” in your home folder and will have its permissions updated automatically.

To allow Gear Lever to automatically update the Appimage, set the source to GitHub and paste the following to always get the latest version directly from the GitHub page:

> https://github.com/galister/wlx-overlay-s/releases/download/*/*-x86_64.AppImage

You should now be notified by gear lever in the future if the appimage has any updates on GitHub, and it will easily allow you to one click update via the GUI.

You can go into Gear Lever's settings and turn on automatic update checking in it's settings.

Then click “Save”. You can check for updates by refreshing metadata at the top of the page.

In the top right of Gear Lever, you can go into settings to set up update notifications for any installed AppImages automatically.

#### CachyOS

Simply install the following AUR package:

> paru -S wlx-overlay-s-git

### wlx-overlay-s Setup

You can automatically set wlx-overlay-s to run automatically once your headset connects to WiVRn.

Go to the main WiVRn dashboard page again.

![WiVRn Dashboard](/assets/images/wivrn_dashboard.webp?msec=1757257046966)

Notice the "Application" field on this page -- this is the default program that WiVRn will run once you connect to your computer.

Set application to custom and enter the following into WiVRn depending on your distro of choice:

#### Bazzite/PikaOS

Change **USERNAME** to match your user account name:

> /var/home/USERNAME/AppImages/wlxoverlays.appimage

#### CachyOS

Just launch the native executable:

> wlx-overlay-s

Note that the first time you connect, a window will pop up on your desktop.

wlx-overlay-s needs to know which monitors you have connected to your computer in a specific order.

Follow the pop up messages in the lower right of your monitor and select your displays in the order it tells you to do so. You only have to do this once.

Once the window selections have completed on the PC, you should be able control your desktops now. wlx-overlay-s has a unique control scheme, and you can find out more about it starting on the[ GitHub page.](https://github.com/galister/wlx-overlay-s?tab=readme-ov-file#the-watch)

I recommend fully reading the GitHub page when you have the time. You can customize your controller bindings, disable the quest pass-through, disable space move, and even set a custom texture background for your environment. All the info is already located at the wlx-overlay-s [GitHub page.](https://github.com/galister/wlx-overlay-s) I won't cover these in the guide as the information is already listed there, and much of the setup is specific to each user's preferences.

## xrizer

Certain games on Steam, like [Half-Life: Alyx](https://store.steampowered.com/app/546560/HalfLife_Alyx/) are dependent upon Valve's own [SteamVR](https://store.steampowered.com/app/250820/SteamVR/). SteamVR actually uses OpenVR under the hood as it's default programming interface and runtime.

SteamVR runs fairly poorly in Linux on newer Proton versions, and most of the time it won't even run at all.

[xrizer](https://github.com/Supreeeme/xrizer) is a re-implementation of [OpenVR](https://github.com/ValveSoftware/openvr) on top of [OpenXR](https://www.khronos.org/OpenXR/). This enables WiVRn to run supported OpenVR games through any OpenXR runtime without running SteamVR.

It's very simple to download and add as the default OpenVR compatibility library in WiVRn, meaning games that normal frequently require OpenVR/SteamVR can be ran directly without the use of SteamVR!

- xrizer is a rewrite of [OpenComposite](https://gitlab.com/znixian/OpenComposite). xrizer is considered immature at this time, but currently enables support for games that OpenComposite struggles with, such as [Half-Life: Alyx](https://store.steampowered.com/app/546560/HalfLife_Alyx/).
  - To learn more about why xrizer exists, visit [Why rewrite OpenComposite?](https://github.com/Supreeeme/xrizer?tab=readme-ov-file#why-rewrite-opencomposite) over at the xrizer GitHub page.

### xrizer Install:

To get started, fetch the latest nightly release of xrizer from the [xrizer GitHub releases page](https://github.com/Supreeeme/xrizer/releases/).

Once the zip file has been downloaded, extract the .zip folder and move the extracted "xrizer" folder to a location that has full permission access to your user account, such as:

> ~/.local/share/xrizer/

Ensure you have the correct folder structure for xrizer. The shared object library file should be located like this if you pasted it correctly:

> /home/USERNAME/.local/share/xrizer/bin/linux64/vrclient.so

### xrizer Setup:

Setting xrizer to run with WiVRn is very simple. In the WiVRn dashboard settings, scroll down to the very bottom of the page and set the "OpenVR compatibility library" to "Custom", and enter the following into the entry field:

> /home/USERNAME/.local/share/xrizer/

Of course adjust USERNAME to match your own username in both above instances.

- NOTE: To update xrizer in the future, just download the latest version and paste to the same location, overwriting any files.

The only SteamVR/OpenVR game I have fully tested is [Half-Life: Alyx](https://store.steampowered.com/app/546560/HalfLife_Alyx/). I find that the game runs far better in WiVRn with xrizer than it does in SteamVR in Windows ever did for me.

## Hardware Tested

Headset: Meta Quest 2 \
CPU: Ryzen 7 7800X3D \
GPU: Sapphire Nitro+ 7800 XT 16GB \
MEM: G.SKILL 2x16GB DDR5 6000 MT/s \
MOBO: GIGABYTE x670 Aorus Elite AX on F35 Bios \
NVMe: Samsung 980 Pro 2TB \
PSU: Corsair RM750 \
Router: Asus RT AX-3000 (can be bought on [Amazon](https://www.amazon.com/ASUS-RT-AX3000-802-11ax-Lifetime-Whole-Home/dp/B084BNH26P?th=1) for around $80 USD.

## Software Tested

### [Bazzite:](https://bazzite.gg/)

Kernel: 6.16.4-104.bazzite.fc42.x86_64 (64-bit) \
DE: KDE Plasma 6.4.4 \
Mesa: 25.2.1 \
Proton: Proton-GE10-15 and Proton-GE Latest

### [CachyOS:](https://cachyos.org/)

Kernel: Linux 6.16.3-2-cachyos \
DE: KDE Plasma 6.4.4 \
Mesa: 25.2.1-cachyos1.3 \
Proton: proton-cachyos and proton-cachyos-slr

### [PikaOS](https://wiki.pika-os.com/en/home)

Kernel: Kernel Version: 6.16.3-pikaos \
DE: KDE Plasma 6.3.6 \
Mesa: 25.1.7 \
Proton: Proton-GE10-15 and Proton-GE Latest

## Games Tested

The follow games have been extensively tested on the previously listed hardware and software by me personally. I have included the exact launch parameters I use in Steam.

### [VTOL VR](https://store.steampowered.com/app/667970/VTOL_VR/)

VTOL VR requires ntsync to run correctly, and enabling it is done the same as any regular flatscreen game -- by added the correct variable to the launch parameters of the game in Steam.

NOTE: These values are *examples*. Make sure you check WiVRn dashboard's main page for the relevant launch parameters to ensure WiVRn can connect to your games correctly.

- ***Vanilla Gameplay***:

> PRESSURE_VESSEL_IMPORT_OPENXR_1_RUNTIMES=1 PRESSURE_VESSEL_FILESYSTEMS_RW=/var/lib/flatpak/app/io.github.wivrn.wivrn/x86_64/stable/68d7958a1999e2762b7d8d36140035b8d7286580b8f0f0c2db4ac0596891f213/files/xrizer PROTON_USE_NTSYNC=1 %command%

VTOL VR has has [unofficial mod loader available on Steam](https://store.steampowered.com/app/3018410/VTOL_VR_Mod_Loader/). Many mods hosted on the Steam workshop page for the mod loader do work in multiplayer. Install the free mod loader from steam and search it's workshop for mods. Once downloaded, run the mod loader and enable mods on an individual basis and then close the mod loader.

You will only need to open the mod loader to enable or disable specific mods.

- ***With Mod Loader***:

> PRESSURE_VESSEL_IMPORT_OPENXR_1_RUNTIMES=1 PRESSURE_VESSEL_FILESYSTEMS_RW=/var/lib/flatpak/app/io.github.wivrn.wivrn/x86_64/stable/68d7958a1999e2762b7d8d36140035b8d7286580b8f0f0c2db4ac0596891f213/files/xrizer PROTON_USE_NTSYNC=1 WINEDLLOVERRIDES="winhttp.dll=n,b" %command% --doorstop-enable true

- **NOTE**:
  - The mod loader MUST use the same proton version that use for the main game. Make sure the proton version in Steam properties for both VTOL VR and the mod loader is identical or you can run into issues with the mods loading correctly.
  - When using the mod loader, you may disable mods and play the vanilla game without having to uninstall the mod loader by simple changing "true" to "false" for the doorstop argument at the end of the launch parameters. Do this to easily switch between modded and vanilla gameplay. You don't have to disable or uninstall mods to play vanilla VTOL VR!
  - When playing with mods in multiplayer, all players must use the exact same mods to be able to play with each other. Also check the VTOL VR mod loader workshop to ensure a mod supports multiplayer. Older mods break, and VTOL VR updates are known to break mods until they are fixed by the mod creators.

### [Tactical Assault VR](https://store.steampowered.com/app/2314160/Tactical_Assault_VR/)

> PRESSURE_VESSEL_IMPORT_OPENXR_1_RUNTIMES=1 PRESSURE_VESSEL_FILESYSTEMS_RW=/var/lib/flatpak/app/io.github.wivrn.wivrn/x86_64/stable/68d7958a1999e2762b7d8d36140035b8d7286580b8f0f0c2db4ac0596891f213/files/xrizer %command% PROTON_USE_NTSYNC=1 %command%

### [Half-Life: Alyx](https://store.steampowered.com/app/546560/HalfLife_Alyx/)

Half-Life: Alyx runs very well with OpenXR and WiVRn. I highly recommend forcing the fidelity level to it's highest setting to prevent pop-in of textures and greatly reduce traversal and rotation stutter during gameplay.

> PRESSURE_VESSEL_IMPORT_OPENXR_1_RUNTIMES=1 PRESSURE_VESSEL_FILESYSTEMS_RW=/var/lib/flatpak/app/io.github.wivrn.wivrn/x86_64/stable/68d7958a1999e2762b7d8d36140035b8d7286580b8f0f0c2db4ac0596891f213/files/xrizer %command% PROTON_USE_NTSYNC=1 %command% +vr_fidelity_level_auto 0 +vr_fidelity_level 3

## Troubleshooting

- If in doubt, clearly check the [requirements](#requirments) and [compromises](#compromises) sections of this guide to make sure you haven't missed or misunderstood anything. Sometimes taking a break is a good idea and coming back later with a clear frame of mind, especially if you are feeling overwhelmed and/or frustrated.
- Lag and/or fast connecting/disconnects, Quality and/or bitrate low:
  - Try restarting your Quest headset. Sometimes Quest headsets can overheat or have software problems or have other issues on the headset side. A reboot of your headset will usually fix these issues. If the issue persists, try completely rebooting your computer and/or rebooting your network/router. If these issues persist, suspect your network has hardware, software, or interference issues.
  - A common issue is that Quest/Meta headsets will drop to a lower WiFi link rate after sleep/resume and get stuck at that rate. I often find my headset will be stuck at 300 MBit or less vs the normal 1200 MBit. Restarting the headset or toggling the WiFi off and back on again in the headset fixes this issue until the next sleep/resume cycle. You can check for this bug in the WiFi menu on your headset by selecting your network details and scrolling down. This doesn't appear to happen with all headsets or access points.
- Still having quality/rate issues?:
  - The most common issue is poor network performance. A good router is required, but so is a good connection between the router and your headset, as is between your computer and the router. Sometimes the air will be over-saturated with too much data traffic, or maybe even your LAN is being overwhelmed or having issues due to faulty hardware/software -- sometimes it could be a faulty ethernet cable. Advanced setup of both wired and wireless networks is not covered by this guide, as that is a very complicated topic by itself. Another issue is poor GPU performance. Give the COMPROMISES section another quick read, and also take into consideration your hardware specs.
    - Note that shared network like common home networks can cause issues. I have a Spectrum WiFI 7 Tri-Band router at home that provides great speeds but has issues with wireless VR due to the other 10 devices sharing the wireless connection.
    - I instead use a dedicated Asus RT AX-3000 in AP mode connected to my desktop on channel 100 (DFS channel) in 80 MHz mode and I get no issues.

## Advanced Network Testing

### OpenSpeedTest

[OpenSpeedTest](https://openspeedtest.com/selfhosted-speedtest) is a free and open-source HTML5 local speedtest that can very easily be installed and ran. A great tool to test your entire network stack including your networking card, ethernet connection, router, wireless signal and headset connection all together in realistic conditions.

While their website can be used to test your Internet connection, we will be downloading and running it manually on our local network to test our local area network. This will NOT test your internet connection as that happens outside your LAN -- we want to test your local area network including your WiFi connection.

#### OpenSpeedTest Installation

In Bazzite, CachyOS, or PikaOS, I recommend going to the [download page](https://openspeedtest.com/selfhosted-speedtest) for OpenSpeedTest and fetching the latest AppImage for the GUI. The installation of OpenSpeedTest will be the same as [wlx-overlay-s](#wlx-overlay-s Install). Simply download and install the AppImage with Gear Lever. Note that due to how it is hosted on their website, you cannot enter a URL to update the GUI like with wlx-overlay-s.

Once installed, simply launch OpenSpeedTest from your application launcher and it will be awaiting connections from any browser.

On all recommended distros the port 3000 should be open by default so long as you don't change any settings, so no port forwarding is required.

#### OpenSpeedTest Usage

OpenSpeedTest should be open on your desktop so it can await connections. To test your WiFi and network, startup your VR headset and stand/sit in your normal playing location. Ensure your router is setup in it's usual location as well so you can fully test the locations of your headset and router for interference.

Now, due to following:

1. Take note of the address listed inside of the server GUI on your desktop. You will need to manually type this in shortly on your headset.
  
2. Put on your headset and ensure you connected to the right network.
  
3. Open the "Browser" app on your headset and navigate to the IP address of the server. Fully type it in manually, including port.
  
  - > http://192.168.1.224:3000?=60s
    
  
  Note that the exact IP will vary for each user. Also note I have appended ?=60s to the end of the URL -- this will make the server perform a 60 second test instead of the default shorter test so we can get better results.
  
4. The webpage should load and show a blue "Start" button in the lower left. Simply click this button to start the speedtest. The test takes about two minutes.
  
5. When finished, you should see the results page similar to this:
  

![OpenSpeedTest Results](/assets/images/openspeedtest.webp?msec=1757264361440)

Since I am using a dedicated AP with only my headset connected, I am getting very good results as shown in the image above. This is also because I have little to no interference and play within line of sight of my router, about 5-6 feet away. These speeds are possible even with longer ethernet cables (25m from PC to router, and 25M from router to main router).

The limiting factor of my network is the 1 Gbit connection from my computer to my router, and my WiFi connection! This ensures a latency and lag free connection while playing.

If you are seeing much lower speeds, first check that all your ethernet cables are working correctly -- if a single twister pair is damaged, your network connection will drop from 1 Gbit to only 100 Mbit, so 1/10th of the normal speed!

## WiFi interference

Wireless is susceptible to interference from other wireless signals from other routers, phones, tablets, and computers. Solid objects like brick, concrete, and even water can fully or nearly fully block these signals.

A clear line of sight between your play space and your router is the best practice. Place your router up as high as possible along a wall, away from corners and away from other solid objects.

Even with all these things considered, if you live in an area that is heavily congested with WiFi signals and traffic such as a multi-level apartment building, you will likely experience signal interference with other networks.

There is a free tool to check for this interference from from your phone. The two I will recommend can be installed from Google Play (I have an android phone and have tested both of these apps.) If you use Apple, you can check your store and search for "WiFi Analyzer" apps to scan the area.

-    [WiFi Analyzer](https://play.google.com/store/apps/details?id=com.pzolee.wifiinfo)
  
  - Free Version and Paid Version with more features (Free version will work fine)
    
  
  Ideally you would have a free 5GHz channel in your area. If you live near many people, most of these channels will already be in use.
  
  The best practices in order of best case scenarios are as follows:
  
  - A clean, unused channel, supporting the highest width supported.
    
    - A shared channel that exactly lines up with another channel, but the conflicting signal is of low quality.
      
      - A shared channel exactly lines up with another channel, but matching signal strengths.
        
  
  Note that having a shared channel isn't a bad thing, so long as the channel is EXACTLY overlapping with yours. channels that share only part of the total channel width as yours will cause packet loss and interference will all channels in that spectrum (including their own!) Non-overlapping channels are best!
  

### Understanding WiFi Channels

Study the following image of 5Ghz Channel Allocations in North America:

![WiFi Channels in North America](/assets/images/wifi_channels.webp?msec=1757265804529)

Note that on most ISP provided and cheap routers, the DFS(dynamic frequency selection) channels listed in orange and yellow above are NOT AVAILABLE. Availability of certain wireless channels also varies by countries due to laws. In most cases, only the channels listed in green are easily available.

With newer routers like the [Asus RT AX-3000](https://www.amazon.com/ASUS-RT-AX3000-802-11ax-Lifetime-Whole-Home/dp/B084BNH26P?th=1) do have DFS channel availability, increasing the amount of WiFi channels you may be able to use. These channels are allowed by the FCC on supported devices, but these channels come with caveats.

- These channels are shared with military aircraft radars, weather station radars, and other military/government equipment. **By federal law, if your router detects any such aircraft or facilities using these channels, your devices MUST change channel right away -- usually to a non-DFS channel, causing an interruption in your connection!**
  
- Only devices tested and certified by the FCC in the United States can be allowed or sold to use these channels.
  

This channel switching cannot be disabled if you use DFS channels, and a failure to auto-switch channels is a violation of federal law, at least in the United States. Only devices that have their signal switching and are approved by the FCC and fully tested may use them as thing signal switching capability must work when needed.

These channels are a great choice if you live far enough away from local airports or radio stations, such as in larger homes or rural areas. Note that any aircraft flying above your location (Even at very high altitudes) use radar to detect altitude and/or weather and may cause issues with using DFS channels.

I personally use DFS channel 100 in 80MHz mode and have had no issues for several years. The nearest airport is more than 30 miles away, and my location has no aircraft flying directly above. I also have only one other WiFi channel in the 5Ghz spectrum in my area, and it is on a free channel and is very weak compared to mine due to the distance to my neighbors.

The only way to know if you these channels are free is to use and test them.

Without DFS channels, the max amount of non-overlapping channels available in an area will be limited to 9 at 20Mhz, 4 at 40Mhz, or 1 at 80Mhz.

This number jump to 25 at 20Mhz, 12 at 40Mhz, or 6 at 80Mhz if you are able to use DFS channels, a huge jump in the availability of clean channels.

If in a saturated network area, do not use the higher widths such as 80Mhz, as this will greatly reduce the amount of channels available to your neighbors. 40Mhz will work fine for VR, you should only use the higher channels width in free areas.

Note that nearly all Android based headsets feature 2x2 antennas, which limit their available bandwidth to HALF of the possible spectrum, as they cannot support the higher widths.

Refer to the following table for the max layer speeds supported by relevant WiFi routers depending on their set channel widths:

| WiFi Generation | 20Mhz | 40Mhz | 80Mhz |
| --- | --- | --- | --- |
| WiFi 5 (AC) Released: 2013 | 174Mbit | 400Mbit | 866Mbit |
| WiFi 6 or 6e (AX) Released: 2021 | 286Mbit | 574Mbit | 1200Mbit |

A quick glances reveals that the bandwidth uses is much more important than the generational uplift gained from WiFi 5 to 6.

20Mhz isn't suited for VR, especially at higher resolutions and bitrates. 40Mhz is the sweetspot. Using 80Mhz will net you a faster connection to your computer and the internet assuming your internet speeds are fast enough, but it isn't required for VR.

Always remember that each step up in channel width uses 2x the channels than the last. So a network setup in 80Mhz width is using the same amount of channels that as 4 20MHz networks.

The sweet spot is at least WiFI 6 AX in 80Mhz, as that nets you the best chance of higher speeds and low latency. Going higher than 80Mhz is pointless because headsets don't support it, and most computers network cards are limited to 1 Gbit ethernet.

I used a WiFI 5 AC router for over a year at 80Mhz (866Mbit) with no issues as well, so older routers are fine unless you need the extra channel availability such as DFS channels.
