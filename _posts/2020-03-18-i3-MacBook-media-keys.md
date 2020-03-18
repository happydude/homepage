---
author: Jason Davis
layout: post
title: Enable MacBook media keys in i3
---

add to ~/.config/i3/config

```ini
#Pulse Audio controls
bindsym XF86AudioRaiseVolume exec pactl set-sink-volume @DEFAULT_SINK@ +2%; exec pactl set-sink-mute @DEFAULT_SINK@ 0
bindsym XF86AudioLowerVolume exec pactl set-sink-volume @DEFAULT_SINK@ -2%; exec pactl set-sink-mute @DEFAULT_SINK@ 0
bindsym XF86AudioMute exec pactl set-sink-mute @DEFAULT_SINK@ toggle

#Media player controls
bindsym XF86AudioPlay exec playerctl play-pause
bindsym XF86AudioNext exec playerctl next
bindsym XF86AudioPrev exec playerctl previous

#Sreen brightness controls
bindsym XF86MonBrightnessUp exec xbacklight -inc 20 # increase screen brightness
bindsym XF86MonBrightnessDown exec xbacklight -dec 20 # decrease screen brightness
```

Source https://askubuntu.com/a/794843/1055233