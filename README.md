# 360 Nadir and Zenith Tool

Cover the tripod at the bottom (nadir) or the top (zenith) of a 360° equirectangular video with a clean patch or your own logo.

Open an MP4, choose the patch colour, shape, size and feathering, and the app renders a new MP4 at the same resolution as the original.

Everything runs in your browser. Videos are never uploaded anywhere.


## Screenshots
**1. Set up the patch.** The preview shows the full frame and a view looking straight down, so you can see exactly what the patch covers. The logo looks stretched in the flat frame; that's normal for 360° video, and the round view shows how it will actually look.

<img width="2560" height="944" alt="app" src="https://github.com/user-attachments/assets/0d0b7c51-402a-479d-8c57-facb4ebf8c8b" />



**2. Check the result.** The rendered video playing in VLC, looking down. The tripod is gone and the logo sits flat on the floor.

<img width="804" height="568" alt="result-vlc" src="https://github.com/user-attachments/assets/83c87f0f-a687-41ea-9360-6eed7f5b7d05" />



## Quick start

1. Download the app. Either:
   - Select the green **Code** button, then **Download ZIP**, and unzip it; or
   - Open `360-nadir-and-zenith-tool.html` in this repository, select the **Download raw file** button (the download icon above the file), and save it.
2. Double-click `360-nadir-and-zenith-tool.html` to open it in **Chrome or Edge** on a desktop or laptop computer.

No install, server or Git knowledge is needed. The app also works offline.

## Using the app

1. **Load video.** Choose an equirectangular MP4 or MOV, or drag it onto the window. The sidebar shows its size, codec, frame rate, bitrate and audio.
2. **Patch.**
   - *Position*: **Nadir (bottom)** to cover a tripod, or **Zenith (top)** to cover the top of the sphere.
   - *Colour*: white, black or a custom colour.
   - *Shape*: circle or square.
   - *Size*: the radius of the patch in degrees from the pole. The dashed line on the preview shows how many pixel rows of the frame it covers.
   - *Feather*: softens the edge of the patch, from a hard edge up to 20°.
3. **Logo (optional).** Select **Import image** to place a PNG, JPEG, WebP or SVG on top of the patch colour. Adjust its scale and rotation. The image is projected so it looks flat, not stretched, in a 360° viewer.
4. **Render.**
   - *Output codec*: **Auto** uses the same codec as the source where your computer supports it. You can also choose H.265/HEVC, H.264/AVC or AV1.
   - *Bitrate*: **× 1.5 (recommended)** is the default (see Tips).
   - *Write 360° metadata*: leave this ticked so YouTube, Facebook and 360 players recognise the file as 360.
   - Select **Render video**. Progress, frames per second and time left are shown as it runs.
5. Select **Save MP4**. The file downloads as `yourvideo_nadir.mp4` or `yourvideo_zenith.mp4`.

The whole app fits on one screen on a desktop or laptop. Use the scrubber above the preview to check the patch at different points in the video before rendering.

## Tips

- Start at a size of about 15–20° for a typical tripod, then adjust while watching the "looking straight down" preview.
- A custom colour picked to match the ground often blends in better than black or white, especially with some feathering.
- Use a square logo with a transparent background. At 100% scale the logo fills the patch.
- **Why re-encode at a higher bitrate?** Your video is already compressed. Compressing it again at the same bitrate loses a little detail, and the fast hardware encoders this app uses are less efficient than a camera's own encoder. Source × 1.5 usually looks the same as the original. Use × 2 for a master copy you'll keep or edit further, or *Match source* if you'll upload to YouTube or Facebook, which re-compress everything anyway.
- Any frame rate is supported, including 23.976, 29.97 and 59.94 fps. The output keeps the source's exact timing.
- Rendering uses your graphics card's video encoder, so speed depends mostly on your hardware. Keep the tab in the foreground while it renders.

## Known limitations

- Needs a browser with WebCodecs video encoding. Chrome or Edge on a computer is recommended. Firefox and Safari may not work, and phones and tablets are not supported.
- Large frames (6K and 8K) generally need H.265 hardware encoding, which most recent graphics cards have. If no encoder supports your video's size, the app says so and you can try another codec.
- The finished video is held in memory until you save it, so very long, high-resolution videos need plenty of RAM.
- Audio is copied unchanged only if it is AAC. Other audio formats are dropped (the app tells you when this happens).
- Spatial (ambisonic) audio metadata, GPS and camera metadata are not copied to the new file.
- The output is 8-bit. 10-bit and HDR video will be converted to 8-bit.
- If your browser can't play the video's codec, the preview shows a sample scene instead. Rendering may still work.

## Created with Claude

This tool was designed and written by [Claude](https://claude.ai), an AI assistant made by [Anthropic](https://www.anthropic.com), through a conversation with the repository owner. The owner directed the project and tested the result.

## Status

This project is shared as-is. It is not actively maintained and contributions (issues, pull requests) are not being accepted. You are free to copy the single `360-nadir-and-zenith-tool.html` file and adapt it for your own use. It has no build step; the two open-source libraries it uses are included inside the file.

Work on copies of your videos rather than your originals.


## License

Released under the [MIT License](LICENSE). You're free to use, copy, modify and share this tool, but it comes with no warranty.

The app includes these open-source libraries, whose licence notices are kept inside the HTML file:

- [mp4box.js](https://github.com/gpac/mp4box.js) for reading MP4 files, BSD 3-Clause License, © Telecom ParisTech/TSI/MM/GPAC Cyril Concolato
- [mp4-muxer](https://github.com/Vanilagy/mp4-muxer) for writing MP4 files, MIT License, © Vanilagy
