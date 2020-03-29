# Personal Markdown Template
This is for formatting the .md files of my GitHub repos. I often look at the preview to find what I want and then copy the raw version from the file.

I can also use this repo as a template.

## Text

[Make a hyperlink](https://www.google.com/).

## Images

You can use this [tutorial](https://gist.github.com/NawalJAhmed/2168f7659c08b6a033e7f6daf8db69a6) to upload images to GitHub.
[This](https://github.com/NawalJAhmed/Markdown-Guide/issues/new) is a direct link to upload. Remember you can also use gifs. [Screentogif](https://www.screentogif.com/) is a great way to take something you see on your desktop and turn it into a gif.

<p align="center">
  <img src="https://user-images.githubusercontent.com/11577850/66669444-8c1a7500-ec25-11e9-9412-ef17a064a5ee.jpg">
  <br>
  <em> Center Text Caption </em>
</p>

## Videos

To use this, you need a link to the video, and you need to capture a still from the video yourself by fullscreening the video and using the snipping tool delayed by 2 seconds.

<p align="center">
  <a href="https://www.youtube.com/watch?v=jNQXAC9IVRw&list=PLBGH6psvCLx46lC91XTNSwi5RPryOhhde
  " target="_blank"><img src="https://user-images.githubusercontent.com/11577850/72564409-a6e03380-387d-11ea-9730-461e5bfb2621.PNG"
  alt="YouTube video demo"/></a>
  <br>
  <em>YouTube Video Demo (Click on Image for Video) </em>
</p>

This is a smaller thumbnail version.

<p align="center">
  <a href="https://www.youtube.com/watch?v=jNQXAC9IVRw&list=PLBGH6psvCLx46lC91XTNSwi5RPryOhhde
  " target="_blank"><img src="https://user-images.githubusercontent.com/11577850/72564409-a6e03380-387d-11ea-9730-461e5bfb2621.PNG"
                         width="500" height="281.25"
  alt="YouTube video demo"/></a>
  <br>
  <em>YouTube Video Demo (Click on Image for Video) </em>
</p>

# Thinkpad T440p Hackintosh Guide
This is a personal guide of how I got **macOS Mojave** on my T440p. There are other famous guides on GitHub that I followed, but this documents what I did and how I fixed the problems I had. If I ever need to install macOS again on a T440p, I can refer to this guide.

- The primary guide I had used was [jloisel's T440p guide](https://github.com/jloisel/t440p). It has useful instructions and links.
- If you ever need more help [the TonyMacx86 T440p guide](https://www.tonymacx86.com/threads/guide-lenovo-thinkpad-t440p.233282/) might help, but I never needed it.
- [The Hackintosh Laptop Guide by RehanMan](https://www.tonymacx86.com/threads/faq-read-first-laptop-frequent-questions.164990/) was extremely helpful in learning the proper way to install kexts and what to do about the not-working webcam. More on that below.

- [HowToGeek's article about Mac keys](https://www.howtogeek.com/183636/how-the-command-and-option-keys-work-on-a-mac/) is good for learning how Mac keyboards work if you are coming from Windows.
- [Keyboardtester.com](https://www.keyboardtester.com/tester.html) will help you figure out which key does what when configuring your keyboard layout.
- [Karabiner Elements](https://karabiner-elements.pqrs.org/) will help you change your modifier keys to a more comfortable and sensible layout.
- [lwouis's Alt-Tab macOS program](https://github.com/lwouis/alt-tab-macos) is great for getting a far more useful Alt-Tab funcionality than the default one on macOS. You can even configure which key is your Alt key which makes it just like Windows.

## Story
I had originally wanted macOS Catalina, but that resulted in several issues:
- Random kernel panics during use that could not be recreated.
- Trackpad and pointer would on random reboots - not work.
- Sleep mode would cause a reboot. Happens on manually activating sleep mode and when closing laptop lid.
- In an attempt to fix sleep mode, the speakers would no longer be recognized with a reboot required to fix it.
- The provided headphone jack fix only worked once per machine start. Meaning you can plug in headphones once and it will work. However, when unplugging and plugging in the headphones again, you would get static so a reboot would be required to fix it.
- Catalina has a different way of installing 3rd party kexts that require Gatekeeper to be disabled. You might need to enable SIP as well. In previous versions, installing kexts is much easier.

So, I decided to swtich to macOS Mojave for the above reasons as well as possible need for 32bit app support:
- The T440p isn't a vey powerful gaming machine and dual-booting in a seperate Windows partition takes time. Parallels is also not a very good alternative.
- If one wants to play games on macOS, many old games are good options; however most are 32bit.

## Installing macOS Mojave
I used the same broken macOS Catalina system I had to create a bootable flashdrive with macOS Mojave on it. I used [jloisel's T440p guide](https://github.com/jloisel/t440p) to learn how to do this.

Apple has a bad habit of removing the quick find of previous operating systems on their App Store. The previous ones are hidden and are only found [in this archive](https://support.apple.com/en-au/HT201260). Go here are select the OS you want. Then scroll down to downloads. For very old versions, they might provide a .dmg file.

**Remember when installing macOS, use APFS instead of HFS+ if you have a SSD.**

