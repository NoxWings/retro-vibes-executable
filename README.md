# Retro Vibes
Retro-Vibes is a 21K Linux x64 intro. This is my very first prod.

Usage:
```
./retro-vibes.out <width> <height> <scaling> [fullscreen]
```
`width` and `height` are integers, `scaling` is a float and `fullscreen` is just an optional param, whenever it is present it will display the demo at fullscreen.

---

Executing `retro-vibes.out` shows a 1920x1080 window with 100% rendertarget scaling:
```
./retro-vibes.out
```

To show it at fullscreen you need to use:
```
./retro-vibes.out 1920 1080 1.0 true
```
---

## Dependencies
It links against libSDL2-2.0.so.0 to create the window and hook into the audio context otherwise Linux has too many combinations X11, Wayland, ALSA, portaudio, gstreamer etc...

## How is it done / How it works
It is using OpenGL 3.3 and I've used some custom tools to develop it but they are extremely simple, nothing fancy.

### Graphics
Everything is done procedurally using signed distance fields, raymarching and the likes. In order to process shaders I can hot reload them to iterate faster.

### Sound
Actually I wanted to use something that was done already but the only option I found was Tunefish which has a GPL license and I'm not ready to show this code mesh xD at least yet.
About the synthesizer it is pretty simple, everything is realtime, nothing is baked. It has the usual oscillators, envelopes and a couple biquad frequency filters. I've used LMMS to compose the audio and made a small tool to get that midi into the executable.

### Compression
I have used what it is already available in a default Ubuntu installation, I'm just using a shell drop with `lzcat` or `xz` [package](http://releases.ubuntu.com/focal/ubuntu-20.04-desktop-amd64.manifest##:~:text=xz-utils) | [files](https://packages.ubuntu.com/focal/amd64/xz-utils/filelist) | [lzcat](http://manpages.ubuntu.com/manpages/focal/man1/xz.1.html)
