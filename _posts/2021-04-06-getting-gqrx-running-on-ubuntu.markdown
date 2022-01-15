---
layout: default
title:  "Getting gqrx running on Ubuntu 20.04"
date:   2021-04-06 10:19:08 -0500
categories: radio
---
I recently became aware that an update to gqrx has introduced a feature to display the band plan on the waterfall. Unfortunately when I went to update, it appeared the most recent version is not in the repos.

You can do the installation of the updated version from github:

https://github.com/csete/gqrx

For this to work on Ubuntu 20.04, I needed a laundry list of prerequisites. Note that since I had gqrx installed from the repository already it may have already installed packages not on this list so there could be more:

qt5-default

gnuradio

gnuradio-dev

libsound2-dev

libasound2-dev

libjack-dev

gr-osmosdr

portaudio19-dev

libpulse-dev

liborc-0.4-dev


With these installed hopefully you can follow the instructions on the repository.


