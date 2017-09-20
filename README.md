## MultiScreener Max 7 version
MultiScreener Max Patches adapted for HD video

## Instructions
**general**
- download Max 7
- download patches
- connect computers on the same network (ethernet preferable)
- open server patch on first computer
- load video, change settings (settings saved automatically)
- open client on second computer
- load video, change settings
- start server video
- videos should play back in sync

**for automated playback on mac**
- set up video playback on server and client
- set automatic start up and shut down times of computer (Mac System Preferences > Energy > Schedule)
- use applescript to load Max and MultiScreener at startup (often needs delays to load properly)
- set auto shut down time in MultiScreener patches, just before Mac computer auto-shutdown, this let's the computer shut down quietly without dialogs

**Background**
This patch was originally created by Zach Poff (https://www.zachpoff.com/software/multiscreener/) to synchronise multiple videos across a network of computers. It functions through a server / client relation where the server sends the current time of its video playback to every client on the network, which then attempts to align its playback. 

Please read the further info on Zach's website.

This update is for Max 7 and using the AV Foundation video engine to enable this to play HD ( 1920x1080 or 1920x1200+ ) video. The main changes from Zach's original version are: 
- changing video object chain to use [jit.qt.movie @colormode uyuv] > [jit.gl.slab @file cc.uyvy2rgba.lite.jxs] > [jit.gl.videoplane] for more efficient playback. This technique was found on the Cycling 74 forums
- Slight alterations to 
- addition of code to set an "auto-shutdown" time where Max will close itself, allowing the computer to nicely shut itself down without error warnings

This has primarily been used for playing video art in gallery contexts where maximum automation is desirable. These patches should automatically sync to each other regardless of which is started first and other factors and allows auto-startup and shutdown.

**Preferences**
You can change the Transmit Interval on the Server. This affects the rate at which timing messages are sent to clients and can slightly reduce overhead.

**File Formats**
Video playback has been tested using Apple ProRes codec. Depending on whether the computer is using a HD or SSD, CPU/Memory/Graphics you may have different results. Typically if using a hard disk, converting your full quality video to Apple ProRes (Proxy) will result in a smaller file size (at the cost of some quality), alternatively if using a solid state drive then Apple ProRes 422 should give better results. Alternatively you can use Photo-JPEG or Apple Animation codecs.
One way to convert videos is to use ffmpeg https://www.ffmpeg.org/

**Tested on**
Mac OS X 10.8 - 10.10
Max 7.3.4 (does not require licence to run)
download from https://cycling74.com/

Generally gives good results on Mac Mini computers.

**Troubleshooting**
If stuck in fullscreen mode, press ESC. If this doesn't work, hold ESC for a few seconds. If still stuck, try clicking on the video window, pressing ESC, clicking again and then holding ESC for a few seconds.

**Licence**
GNU General Public Licence (GPL)
This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program.  If not, see <http://www.gnu.org/licenses/>.

NOTE: Max7 is proprietry software and is required to run these patches

# Bugs, suggestions, comments
Please email to kt@negativespaces.net, or feel free to download and adapt.
