---
layout: post
title: Openbox Configuration
categories: linux
comments: true
---

In the Linux community we enjoy sharing our desktop configuration. There
couldn't be a better time to be using Linux. I'd say that KDE Plasma and 
Gnome desktops are very
usable now and I like them both, but prefer KDE. However, I dont use 
either, I have been content with openbox. If you use a login manager
openbox will read its startup program list from ~/.config/openbox/autostart.
But, if you use startx you will need to add your startup programs to
~/.xinitrc.

Here is my openbox autostart file.

~~~
albert &
pasystray &
nitrogen --restore &
tint2 &
~~~

* albert - this is an application launcher. On first run you will need to set 
  its keystroke sequence. I use ctrl + space, and that doesn't seem to 
  conflict with anything. 
* pasystray - pulse audio tray for configuring sound and mic settings
* nitrogen - sets desktop wallpaper
* tint2 - a very configurable toolbar

You will want to do 2 important things now:

1. set up openbox menu
2. configure tint2

# obmenu-generator

A static menu is slightly more responsive, but you need to 
re-generate your menu if new software is added.

~~~
$ cd ~/.config/openbox
$ obmenu-generator -s > menu.xml
~~~

# tint2rc

You might want to add launchers for your most frequently used programs.
.desktop files are act as shortcuts to programs and provides icons etc.

~~~
launcher_item_app = /usr/share/applications/google-chrome.desktop
launcher_item_app = /usr/share/applications/xfce4-terminal.desktop
launcher_item_app = /usr/share/applications/Thunar.desktop
~~~

I also prefer the bar on the top of the screen, the reason being is the mouse
pointer is more likely to be near the top of the screen and I like to minimize
the distance the mouse has to move in general. I also like to use autohide.

~~~
panel_position = top center horizontal
autohide = 1
~~~

The laptop battery indicator built into tint2 shows up when you have a charge
percentage lower than the value for battery_hide.

~~~
battery_hide = 95
~~~

# xfce4-mime-settings 

One thing that can be frustrating in Linux at this point can be setting your
default applications. Especially since there doesn't seem to be a default 
file browser set on a fresh install.

I use xfce4-mime-settings to set my default applications in openbox. 
Set inode/directory to thunar.

![xfce4-mime-settings](/images/Screenshot_20170127_104050.png)

# kate

Check out this editor. It has been around a long time now and is very good. You will 
need to add hunspell to your install to get spell checking. Kate has decent support
for projects that use git. It is lightning fast compared to atom or sublime. This
is my pick for a text editor. 


# mypaint

If you have a tablet or touchscreen you will want this program. It is the closest
thing to pen and paper I can find. Mypaint uses the keyboard a lot, it is worth
while to learn the keys:

shift - draw a line
z - undo
d - smaller pen
f - bigger pen
'-' - zoom out
'+' - zoom in
r - pick color
x - recent colors
e - eraser

![mypaint](/images/Screenshot_20170127_105831.png)

# spectacle

A less geeky simple screenshot utility.


{% if page.comments %} 
 
<div id="disqus_thread"></div>
<script>
var disqus_config = function () {
this.page.url = 'http://designr8.com/android/2017/01/26/openbox-configuration.html'; 
this.page.identifier = 'openboxconfiguration';
};

(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = '//openboxconfiguration.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
                                
{% endif %}

