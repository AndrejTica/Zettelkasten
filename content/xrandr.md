---
date: 2025-03-14
tags:
  - linux
  - "#todo"
---
To configure screen resolution, do the following:

```
$ gtf 1920 1080 60

  # 1920x1080 @ 60.00 Hz (GTF) hsync: 67.08 kHz; pclk: 172.80 MHz
  Modeline "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync

$ xrandr --newmode "1920x1080" 172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
$ xrandr --addmode VGA1 1920x1080
```
This is in the case that there is no mode that matches your screen resolution.

### gtf



### References
[Generalized Timing Formula - Wikipedia](https://en.wikipedia.org/wiki/Generalized_Timing_Formula)


