DASH-VR Player
================
This player lets you watch **DASH format** or ordinary 360 flat video or on your Oculus Rift or Android device with VR headset (Cardboard, Durovis Dive, etc.) from a web browser. 

Declaration:
This player is extend from eleVR and DASH-JS.

**eleVR**: https://github.com/hawksley/eleVR-Web-Player

**dash.js**: https://github.com/Dash-Industry-Forum/dash.js

-

Test Environment 
================
- ```dash.js```: To check if your browser supports dash.js please see: http://caniuse.com/#feat=mediasource
- ```WebGL```: Many browsers support WebGL now, like Firefox, Chrome and Safari.

**Note**: Currently, for mobile devices, Android Chrome (50+) can be used (dash.js do not support Safari or Chrome on IOS). 
 

-

Make Your Own DASH Format Video
================

**Transcoding and resizing using ffmpeg**. The instruction is like:

```
ffmpeg -i input.mov -s 640x360 -c:v libx264 -b:v 600k -r 24 -x264opts keyint=48:min-keyint=48:no-scenecut -profile:v main -preset medium -movflags +faststart -c:a libfdk_aac -b:a 128k -ac 2 out-low.mp4
```

See details: https://www.radiantmediaplayer.com/guides/working-with-ffmpeg.html

**Segmentation using MP4Box**. The instruction is like:

```
MP4Box -dash-strict 4000 -rap -bs-switching no -profile dashavc264:live -out manifest.mpd out-low.mp4#audio out-low.mp4#video out-med.mp4#video out-high.mp4#video
```

See details: https://www.radiantmediaplayer.com/guides/working-with-mp4box.html

**Note**: DASH-IF suggest that do not use ```-bs-switching no```. See https://github.com/yyakult/dash.js/wiki


-



