# Thinkpad T440p Hackintosh Guide

![GitHub last commit](https://img.shields.io/github/last-commit/NawalJAhmed/T440p-Hackintosh?color=blue&label=last%20commit%20was&logo=googlecalendar&logoColor=red&style=flat-square) ![GitHub forks](https://img.shields.io/github/forks/NawalJAhmed/T440p-Hackintosh?color=gree&label=forks&logo=github&style=flat-square) ![GitHub User's stars](https://img.shields.io/github/stars/NawalJAhmed?color=purple&label=total%20stars&logo=github&style=flat-square) ![Twitter Follow](https://img.shields.io/twitter/follow/NawalJahmed?label=Follow%20Me%20%40NawalAhmed&style=social)

<p align="center">
  <img src="https://user-images.githubusercontent.com/11577850/77968905-7291e600-72b6-11ea-886d-b1726e576b5a.png">
  <br>
  <em> 99% Working T440p Hackintosh Running macOS Mojave. 1920x1080p IPS Mod, 3 Button Trackpad Mod, Backlit Keyboard Mod, Ultrabay SSD Mod, i7-4810mq CPU Replacement Mod, and WiFi from TP-Link TL-WN725N Dongle with a WiFi icon mod. Note that while the wallpaper is Catalina, the OS is Mojave. I just like the Catalina wallpaper.</em>
</p>

---

**Read everything in this guide.**

This is a personal guide of how I got **macOS Mojave** on my T440p. There are other famous guides on GitHub that I followed, but this documents what I did and how I fixed the problems I had. If I ever need to install macOS again on a T440p, I can refer to this guide.

- The primary guide I had used was [jloisel's T440p guide](https://github.com/jloisel/t440p). It has useful instructions and links. I do not however recommed his One Key HiDPI install recommendation even for 1920x1080p displays. By default, scaling is fine. If it is too compressed for you, then sure install it.
- If you ever need more help [the TonyMacx86 T440p guide](https://www.tonymacx86.com/threads/guide-lenovo-thinkpad-t440p.233282/) might help, but I never needed it.
- [The Hackintosh Laptop Guide by RehanMan](https://www.tonymacx86.com/threads/faq-read-first-laptop-frequent-questions.164990/) was extremely helpful in learning the proper way to install kexts and what to do about the not-working webcam. More on that below.
---
- [HowToGeek's article about Mac keys](https://www.howtogeek.com/183636/how-the-command-and-option-keys-work-on-a-mac/) is good for learning how Mac keyboards work if you are coming from Windows.
- [Keyboardtester.com](https://www.keyboardtester.com/tester.html) will help you figure out which key does what when configuring your keyboard layout.
- [Karabiner Elements](https://karabiner-elements.pqrs.org/) will help you change your modifier keys to a more comfortable and sensible layout.
- [lwouis's Alt-Tab macOS program](https://github.com/lwouis/alt-tab-macos) is great for getting a far more useful Alt-Tab funcionality than the default one on macOS. You can even configure which key is your Alt key which makes it just like Windows.

## Story

### Issues with macOS Catalina
I had originally wanted macOS Catalina, but that resulted in several issues:
- Random kernel panics during use that could not be recreated.
- Trackpad and pointer would on random reboots - not work.
- Sleep mode would cause a reboot. Happens on manually activating sleep mode and when closing laptop lid.
- In an attempt to fix sleep mode, the speakers would no longer be recognized with a reboot required to fix it.
- The provided headphone jack fix only worked once per machine start. Meaning you can plug in headphones once and it will work. However, when unplugging and plugging in the headphones again, you would get static so a reboot would be required to fix it.
- Catalina has a different way of installing 3rd party kexts that require Gatekeeper to be disabled. You might need to enable SIP as well. In previous versions, installing kexts is much easier.
- Ultrabay HDD/SSD was not detected and I would get an error at the start of every startup.

So, I decided to switch to macOS Mojave for the above reasons as well as possible need for 32bit app support:
- The T440p isn't a vey powerful gaming machine and dual-booting in a separate Windows partition takes time. Parallels is also not a very good alternative for gaming.
- If one wants to play games on macOS, many old games are good options; however most are 32bit.

## Installing macOS Mojave
I used the same broken macOS Catalina system I had to create a bootable flashdrive with macOS Mojave on it. I used [jloisel's T440p guide](https://github.com/jloisel/t440p) to learn how to do this.

jloisel's repo links to a useful guide on how to create a bootable USB installer for macOS. [This Hackintosher article](https://hackintosher.com/guides/how-to-make-a-macos-10-14-mojave-flash-drive-installer/) is the guide on how to make a bootable installer and [This is an archive](https://web.archive.org/web/20190324220653/https://hackintosher.com/guides/how-to-make-a-macos-10-14-mojave-flash-drive-installer/) of that incase it ever gets deleted.

Apple has a bad habit of removing the quick find of previous operating systems on their App Store. The previous ones are hidden and are only found [in this archive](https://support.apple.com/en-au/HT201260). Go here are select the OS you want. Then scroll down to downloads. For very old versions, they might provide a .dmg file.

**Remember when installing macOS, use APFS instead of HFS+ if you have a SSD.**

## Installing Kexts
After macOS is installed using the instructions given by jloisel, you need to install 3rd party kexts so your touchpad and webcam will work.

[The Hackintosh Laptop Guide by RehanMan](https://www.tonymacx86.com/threads/faq-read-first-laptop-frequent-questions.164990/) tell's you how to install kexts.

**Do not install the custom USBPorts.kext that jloisel has in his EFI folder as of release version 2.2.0. It will cause your webcam to stop working. instead install USBInjectAll.kext from release version 2.1.0, which can be found [here](https://github.com/jloisel/t440p/releases).**

**Note that the docking station might not work if you use this fix. I do not have a docking station anyway.**

## Fixing The Webcam
See the above bold text. If you did not pay attention to it and installed the custom USBPorts.kext anyway, you need to remove it and install USBInjectAll.kext. [RehabMan's Laptop Guide](https://www.tonymacx86.com/threads/faq-read-first-laptop-frequent-questions.164990/) shows you how to do this too.

## Fixing The Keyboard Layout
After first installing macOS, you will be asked to identify your keyboard. Ignore and close this.

At this point, I need to tell you that I am one of those people that switches the Fn key with the Control Key for Windows. I also like to have the FnLock active. That means for instance, the key farthest away from is the key I use for copy and pasting. Control key becomes the Fn key so I can for instance use that and F1 to mute volume.

With that in mind, below is the key configuration I use.

Symbols:
- ⌘ is Command which is the equivalent of Control in Windows.
- ⌥ is Option/Alt which is the equivalent of Alt in Windows.
- ⌃ is Control which is not used that much. Used to be used for right click back when Macs had one button mice.

By default:
- Left Alt key is Command (⌘) action
- Windows key is Alt/Option action (⌥) (Option is also called the Alt key)
- Fn key is Control (⌃) action
- Left Control is Fn action for audio and brightness controls
- Right Control is Control (⌃) action
- Right Alt is Command (⌘) action
- Insert Key does not work at all. Mac keyboards do not have a Insert key, instead they replaced it with an Fn key. However on [Keyboardtester.com](https://www.keyboardtester.com/tester.html), the Insert key is not detected at all.

Use [Keyboardtester.com](https://www.keyboardtester.com/tester.html) to test out what key does what.

Use [Karabiner Elements](https://karabiner-elements.pqrs.org/) to change the modifier keys. Do not configure it using System Preferences.

Modifications:

<p align="center">
  <img src="https://user-images.githubusercontent.com/11577850/77873466-0f517680-7218-11ea-8623-b9cc8e56fee3.png">
  <br>
  <em> Karabiner Elements Simple Modifications </em>
</p>

- Windows Key in now Control (⌃) action
- Fn Key is now Command (⌘) action
- Left alt key is now Alt/Option (⌥) action
- Left Control Key is still Fn action for audio and brightness controls
- Right Control Key is now Command (⌘) action
- Right Alt Key is now Alt/Option (⌥) action
- Insert key still has no action

You might not need this, but I also changed the top Function keys to the defaults:

<p align="center">
  <img src="https://user-images.githubusercontent.com/11577850/77873672-af0f0480-7218-11ea-9c43-8f63933991ba.png">
  <br>
  <em> Karabiner Elements Function Keys </em>
</p>

## Stop Updates
Hackintoshes have trouble updating, so I like to stop automatic updates and checking until I know it will work. The issue however is that you will get a red notification on System Settings constantly reminding you of an update. To stop this, I took the advice from this [stackoverflow answer](https://apple.stackexchange.com/questions/344278/how-can-i-disable-the-red-software-update-notification-bubble-on-the-system-pref).

## Getting WiFi and Changing the Ugly Icon

Since the internal wifi card that is on the T440p does not work, you will need a USB wifi dongle like the [TL-WN725N](https://www.tp-link.com/us/home-networking/usb-adapter/tl-wn725n/). If you do not want a dongle and still want to use an internal wifi card, you will need to use the DW1820A wifi card and follow [jloisel's T440p guide](https://github.com/jloisel/t440p). However, this card costs a lot of money and the [TL-WN725N](https://www.tp-link.com/us/home-networking/usb-adapter/tl-wn725n/) is much cheaper and works great.

Once you have the dongle and install the drivers through the link provided, then you will see wifi icons that look like the following below:

<p align="center">
  <img src="https://user-images.githubusercontent.com/11577850/78077364-4178ea80-7376-11ea-89ad-732867529224.png">
  <br>
  <em> lwouis's alt-tab-macos program preview </em>
</p>

It does not fit the style of the rest of the finder bar like the regular wifi icon. Luckily you can change the icon to the default one thank to these two links:

1. [yunyu's OSXRealtekWifiIcons](https://github.com/yunyu/OSXRealtekWifiIcons)
2. [Abisai's post on tonymacx86](https://www.tonymacx86.com/threads/change-the-color-bars-tp-link-dongle-to-the-wifi-icon.259546/)

I recommend you use the first link as it has icons for both light and dark mode. But the second link works well too. Once the icons are replaced and restarted, the icon will look like this:

<p align="center">
  <img src="https://user-images.githubusercontent.com/11577850/78078546-63736c80-7378-11ea-8aa3-e40c769b100f.png">
  <br>
  <em> Correct WiFi icon </em>
</p>

However since Mojave does not have automatc dark mode theme switching like Catalina does, if you want to switch to dark mode and keep a consistency with the WiFi icon, you need to manually replace the icons and restart the machine.

## Better Alt-Tab
I don't like how the default Alt-Tab is handled in macOS. It does not show previews of the windows nor does it show all of the windows for an app nor does it show the minimized windows.

<p align="center">
  <img src="https://user-images.githubusercontent.com/11577850/78076382-4f2d7080-7374-11ea-9827-96e6aaa7b0aa.jpg">
  <br>
  <em> lwouis's alt-tab-macos program preview </em>
</p>

[lwouis's alt-tab-macos program](https://github.com/lwouis/alt-tab-macos) works very well. You can set the preferences for the Alt action to be set by the Alt/Options key so that plus Karabiner Elements will allow you to use normal Alt+Tab on your keyboard for this program. If you want the normal macOS Alt-Tab function, you can still use Fn+Tab on your keyboard.

<p align="center">
  <img src="https://user-images.githubusercontent.com/11577850/77877940-25b1ff00-7225-11ea-8ec5-13624cd38242.png">
  <br>
  <em> lwouis's alt-tab-macos program preferences </em>
</p>

## Hide Status Bar Icons

By this point you have Karabiner Elements and Alt-Tab macOS in your finderbar. You probably will not need access to them all the time, so you may want to hide them. A popular tool for hiding apps in your finderbar is Bartender. While Bartender is nice, there is a free and open-course app called [Dozer](https://github.com/Mortennn/Dozer) that does the same thing.

<p align="center">
  <img src="https://user-images.githubusercontent.com/11577850/78096348-54f07980-73a7-11ea-9315-7a79394c3ba0.gif">
  <br>
  <em> Dozer Demo </em>
</p>

## Window Snapping

One good feature that Windows and most Linux distros have had for a long time is window snapping when you move a program to an edge or corner of a screen and it automatically resizes it so you can have several programming at the front of the screen. You can also use your keyboard as well. macOS does not have this by default and a popular program that does this is Magent. However it is a paid-for application. A good alternative that does the same thing is called [Rectangle](https://github.com/rxhanson/Rectangle). It is free and open-source and is based on the popular now discontinued Spectacle.

If you want something a bit more advanced and Linux-like, then use [Amethyst](https://github.com/ianyh/Amethyst) which is automatic tiling that mimics xmonad. It automatically resizes opened windows according to pre-defined layouts so you may not want that if you easy control and don't want to have to rely on key commands to resize windows.

Alternatives are [yabai](https://github.com/koekeishiya/yabai) and [Tiles by Sempliva](https://freemacsoft.net/tiles/) which is free but not open source.

<p align="center">
  <img src="https://user-images.githubusercontent.com/11577850/78097724-fcbb7680-73aa-11ea-81c4-839f6a6bfbb8.gif">
  <br>
  <em> Note: This gif is actually Magnet, not Rectangle. I was too lazy to make a gif on my own so I found this. But Rectangle looks very close to this and does the exact same thing. </em>
</p>


## Battery Length
This isn't exactly highly scientific testing, but I wanted to see how well the 9-cell battery performed and how well sleep is on macOS. This is an almost new battery. Very light use for about 2 months.

Battery life lasts about 5 hours on full brightness doing moderate work. This is without watching YouTube, Plex or any other video which is a good way to drain your battery fast.

I have not tested yet how long the battery lasts while watching video.

Sleep mode works great. I let the laptop sleep for 6 hours and 43 minutes and the battery only decreased by 6%. That is a decrease of 0.8% per hour. Waking up from sleep is very fast and prompts for a password. Wifi is turned off during sleep.

## What Works
- 3 Button Touchpad and middle click
- Touchpad gestures up to 3 fingers.
- Pointer
- Webcam
- Microphone
- Sleep
- Headphone jack
- Brightness control
- Audio control
- Configured keyboard
- Displayport

## Not Tested If Working
- VGA (likely won't work since actual Macbooks don't have VGA)
- Card Reader (jloisel's repo has instructions on how to get it working but I never need the card reader anyway)
- Docking Support (do not own a docking station and it might not work due to the rollback of USBInjectAll.kext to make the webcam work)
- iMessage and Facetime (do not own an iPhone so I never used iMessage or Facetime.)

## Does Not Work
- iCloud (keep getting an error of "Account limit reached" when I try to sign into iCloud which makes no sense as this is the only device I have with Apple software. Not a big deal as there are plenty of other cloud services.)
