
# SheffJam VI Dashboard
## Introduction
A Reveal.JS powered slideshow with countdown timer and Figlet title card.
The original Tmux style dashboard utilised in previous SheffJams needed to be replaced with a more readable and easy to setup solution. This style of dashboard goes some way towards achieving those goals.

### Technologies Used: 

 - Reveal.JS is provided under the MIT license (https://github.com/hakimel/reveal.js)
 - Figlets were generated with [Patrick Gillespie's Figlet Generator](http://patorjk.com/software/taag/#p=display&f=Graffiti&t=Type%20Something%20), using the Doh font, any other Figlet generator would also work
 - To actually display the dashboard, we used a Raspberry Pi, but any hardware that can run a modern web browser should also work.  
 
 ### Added Code Features
 - Countdown timer at the bottom of /js/reveal.js (line 6029 onwards)
 - Twinkling star background in the stars.html file are iframe-d in as the background
 - Slides content is in index.html
 - Some of the default flags in /js/reveal.js are modified to better suit a headless full-screen dashboard. Autoslide, loop, and control hiding were some of the values changed.

## Instructions
#### Quick Note
These slides won't be directly usable for further GameJams (the countdown timer will display negative values). Also, the publicity theme for SheffJam VI was "XP by Night" and so you should use slides and backgrounds which reflect the new publicity theme, but not the GameJam theme as this is kept secret until the day. Play around with some of the values preset such as the countdown date and Reveal.JS settings.

 1. If you're using a Raspberry Pi:
	 - Download and flash Debian to the Raspberry Pi ([Link to distros](https://www.raspberrypi.org/downloads/)). You could use Ubuntu MATE but these instructions might need to be adapted.
	 -  Add `consoleblank=0` to the /boot/cmdline.txt file to disable screen blanking, if you don't do this you'll need to wiggle the mouse to keep the dashboard on.
	 - Move the contents of the Dashboard folder to /boot.
	 -  Boot the Raspberry Pi, there's no need to download any additional software. Unless Chromium isn't preinstalled: `sudo apt-get install chromium-browser`
	 - Open the Raspberry Pi's config and enable SSH. This will allow you to edit the dashboard remotely, and simply refreshing the page to load new content.
 2. If you're using anything else:
	 - *Reconsider leaving any personal laptops/machines unattended for displaying dashboard*
	 - Ensure your display is not set to time out or use any screensavers.
	 - Connect your machine to the TV/projector
	 - Display only on the output monitor to prevent screen burn.
	 - Provided that you have a modern web browser like Firefox or Chrome installed - you can just click on index.html
 3. The contents of the dashboard will need to be changed over the course of the day. Consider having meal times, minigames, prize information, hackerrank style challenge URLs and other useful information updated to the dashboard.
	 - If you're using a Raspberry Pi, [set up a hotspot](https://support.microsoft.com/en-gb/help/4027762/windows-use-your-pc-as-a-mobile-hotspot) and use `ssh pi@ip.address.of.rpi` to access the terminal without disrupting the screen.
	 - Use the nano tool to edit the sections
		 - `~$ nano /boot/yourdashboard/index.html`
	 - I understand that GUI editors are better, but using VNC/RDP on a Raspberry Pi on a mobile hotspot is not going to be a good experience.
	 - Add further `<section>` tags to display extra slides. You can use HTML and Reveal.JS formats it for you. The one thing Reveal does not do is stop text from flowing past the bottom of the screen, so keep sections brief!
 4. There's full support for HTML in the slides, so you could have actually live information pulled from, say, Twitter if you wanted to. This wasn't done for SheffJam VI, mainly due to recently restricted Twitter embedding tools. Consider how many people will actually use this before investing time in these extra bells and whistles.
# Bugs
The only bug is that the star's image file is pulled from the Internet. If your dashboard's machine doesn't have Internet when loading, the background will simply be pitch black. You can disconnect the Raspberry Pi from the Internet once the page has loaded.
