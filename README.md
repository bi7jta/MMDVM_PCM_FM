# MMDVM_PCM


Detail info  http://www.dudetronics.com/index.php/dude-star-radio-project

DudeTronics
DUDE-Star Radio Project
 
DUDE-Star software is an open source application for amateur radio operators that allows RX and TX of D-Star, DMR, YSF, NXDN, and P25.  It supports all known USB AMBE vocoder devices, and also supports experimental RX and TX of all modes using software vocoder algorithms.  The software is located here:

https://github.com/nostar/dudestar

DUDE-Star hardware is a project I've been working on to allow an analog radio to be used as a multi-mode digital transceiver when used in conjunction with the DUDE-Star software.  The hardware is similar to an MMDVM Radio interface except it includes an AMBE-3000 vocoder. My end goal was to create a stand-alone black box solution with an audio interface and a configuration interface like a web interface and/or touch screen.  Ultimately I decided not to re-invent the wheel and instead, I have implemented utilities for PiStar to provide this functionality.  When used with a MMDVM board like described below connected to the 9600bps data port of a so equipped analog radio, and some minor modifications to the MMDVM board for PTT control, the analog radio becomes multi-mode digital capable.

The utilities are called XXX2PCM, where XXX is one of the digital modes, and PCM is Pulse Coded Modulation, aka raw audio. P252PCM uses open source imbe vocoder algorithms, and works very well.  YSF2PCM uses the md380 firmware for vocoding, and works very well.  DSTAR2PCM requires a USB AMBE vocoder device, and works very well.  DMR2PCM uses the same md380 firmware vocoding as YSF, but does not work with Tier 2 DMR.  For our interest as hams, that essentially means with repeaters.  Tier 1 (simplex) works great, but repeaters can only be received.  The high speed switching between RX and TX required by Tier 2 DMR is something that can not be created with regular analog radios, so I don't think this will be possible in the future.

Ultimately I hope to see all of this included in a future PiStar release, but in the meantime I have provided a demonstration video and instructions for the Linux savvy and fearless PiStar user to set this up themselves.  This is nowhere near production ready and is only meant for other developers and testers. It will be very easy and probable to break your PiStar software attempting this, so always make backups.  There will be no support in any way, shape, or form other than this document.  Most people reading this should wait for this stuff to be rolled into a future PiStar release, or possibly a PiStar fork.

Hardware requirements

Functional PiStar system with RPi >= v2.
MMDVM Radio board
FM Transceiver with 9600 DIN-6 data connector
DIN-6 cable

Software requirements (some will replace existing instances already in Pistar)

Up to date PiStar installation
imbe_vocoder https://github.com/nostar/imbe_vocoder
md380_vocoder https://github.com/nostar/md380_vocoder
MMDVM_PCM https://github.com/nostar/MMDVM_PCM
MMDVMHost https://github.com/nostar/MMDVMHost
P25Clients https://github.com/nostar/P25Clients
YSFClients https://github.com/nostar/YSFClients
PiStar dashboard patch http://www.dudetronics.com/radio/configure.diff
