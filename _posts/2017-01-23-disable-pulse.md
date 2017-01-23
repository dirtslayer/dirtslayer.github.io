---
layout: post
title: Using separate users to disable pulseaudio
categories: linux
---

I use pulsaudio when I am not using applications that dont support it well. So most things for everyday stuff. But when I am using midi sound system or certain sound applications (fmit) I like an alsa setup, which means [disabling pulseaudio][running pulse].

I create a separate user for that, this way configs do not have to be swapped, we just logout and login as a different user. Use systemctl as the new user that you want to disable pulse with. Arch linux documentation - [disabling pulseaudio][running pulse].
'''
$ systemctl --user mask pulseaudio.socket
'''


fmit is a free musical instrument tuner that does not support pulse, but works great with alsa.

Now to use fmit we just need to set our alsa device, which is easy if you know how to find the incantation of arecord -l.

~~~
[darrell@archdd ~]$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 2: ALC892 Alt Analog [ALC892 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: C920 [HD Pro Webcam C920], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
~~~

My recording mic is on my webcam, C920, we can see that at the moment it is card2, device 0. wich in alsa speak is hw:2,0

![fmit settings][images/2017-01-23-132940_1920x1080_scrot.png]

![hydrogen settings]

![jsampler settings]

[running pulse]: https://wiki.archlinux.org/index.php/PulseAudio#Running

