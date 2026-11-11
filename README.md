# X Media Gallery — Download Photos & Videos

A Chrome extension that turns your X (Twitter) timeline into a media-first gallery and lets you download any photo or video in one click. Videos save as a single MP4 **with sound**.

[**Install from the Chrome Web Store**](https://chromewebstore.google.com/detail/x-media-gallery-%E2%80%94-downloa/elblpcbpknpdgfpbgoflmamfpnknjaja) · Current version: **0.8.3** ([release notes](https://github.com/stin90/x-gallery/releases/tag/v0.8.3))

Click the extension icon and the page flips into a gallery of every image and video from the tweets you've loaded. Scroll and the underlying timeline keeps loading more. Click again to return to the normal timeline.

![X Media Gallery screenshot](assets/screenshot-1-1280x800.png)

## Features

- **One-click download.** Save any image or video from the full-screen viewer. Images download at original resolution. Videos download with sound: X serves audio as a separate stream, so the extension combines audio and video into one MP4 in your browser, with no server and no re-encoding.
- **One-click toggle.** Switch between timeline and gallery from the toolbar icon, or press `Ctrl+Shift+G`.
- **Masonry or grid layout.** Masonry (the default) keeps each item's aspect ratio, so tall and wide media show fully. Switch to a square grid at any time, and use **+ / −** to resize tiles.
- **Hover to preview.** Videos play with sound on hover. In grid view the clip pops out at its native aspect ratio.
- **Filter and search.** Show All, Photos only, or Videos only, and search loaded media by `@handle` or post text.
- **Full-screen viewer.** Step through all media with arrows or the keyboard. Each item shows the author, their @handle, and the post text.
- **Open the original post.** A "View post" link on each tile and in the viewer.
- **Autoplay toggle.** Off (light on resources) or On (every visible video plays muted).
- **Infinite scroll.** The gallery grows as the timeline loads more, without skipping posts on long feeds.
- Works on the home timeline and profile feeds. Layout, filter, tile size, and autoplay preferences are remembered.

### Keyboard shortcuts (viewer)

| Key | Action |
| --- | --- |
| `←` / `→` | Previous / next item |
| `Esc` | Close viewer |
| `D` | Download |
| `Enter` | Open the post on X |
| `Space` | Play / pause |
| `M` | Mute / unmute |

## What's new in 0.8.3

- **Grid stays smooth as you scroll deeper.** The hover pop-out now tracks only the hovered tile instead of re-measuring every tile on each scroll frame ([#1](https://github.com/stin90/x-gallery/issues/1)).
- **Balanced masonry columns.** Tiles reserve their real aspect ratio up front, so new media goes to the shortest column instead of piling into the rightmost one ([#1](https://github.com/stin90/x-gallery/issues/1)).
- **No more missed posts on long feeds.** Loading more now steps through the timeline instead of jumping to the bottom, so posts X unloads off-screen are still captured ([#2](https://github.com/stin90/x-gallery/issues/2)).

## Install

### From the Chrome Web Store

[X Media Gallery — Download Photos & Videos](https://chromewebstore.google.com/detail/x-media-gallery-%E2%80%94-downloa/elblpcbpknpdgfpbgoflmamfpnknjaja)

### From a release zip

1. Download `x-gallery-v0.8.3.zip` from the [latest release](https://github.com/stin90/x-gallery/releases/latest) and unzip it.
2. In Chrome, open `chrome://extensions` and enable **Developer mode** (top right).
3. Click **Load unpacked** and select the unzipped folder.

### Load unpacked (development)

1. Clone this repo:
   ```
   git clone https://github.com/stin90/x-gallery.git
   ```
2. In Chrome, open `chrome://extensions`
3. Enable **Developer mode** (top right)
4. Click **Load unpacked** and select the cloned folder

## Usage

1. Open [x.com](https://x.com)
2. Click the X Media Gallery toolbar icon (or press `Ctrl+Shift+G`) to enter gallery view
3. Use the top bar to switch layout, resize tiles, filter, search, and toggle autoplay
4. Hover a video to play it with sound. Click any item to open the full-screen viewer, and press `D` to download.
5. Click the icon again (or the **Close** button) to return to the normal timeline

## Permissions

| Permission | Why |
| --- | --- |
| Host access (`x.com`, `twitter.com`, `video.twimg.com`) | Read media from your timeline and load video streams for playback and downloads |
| `webRequest` | Observe video stream URLs locally so the gallery can play and download videos. URLs stay in memory and are never transmitted. |
| `storage` | Remember your preferences (layout, filter, tile size, autoplay) between sessions |

See [PRIVACY.md](PRIVACY.md) for the full privacy policy.

## How it works

The content script reads tweet articles already on the page, extracts media URLs, and renders a fixed-position overlay grid. For videos, the background service worker observes `.m3u8` requests made by X's own player and forwards them to the content script, which plays them inline using [hls.js](https://github.com/video-dev/hls.js). Downloads fetch the video and audio streams from X's CDN and combine them into an MP4 locally. Nothing leaves your browser.

## Support

X Media Gallery is free, open source, and ad-free. If it's been useful, you can support development:

- ❤️ [GitHub Sponsors](https://github.com/sponsors/stin90)
- ☕ [Ko-fi](https://ko-fi.com/stin90)
- 🧡 [Buy Me a Coffee](https://buymeacoffee.com/stin90)
- 💸 [PayPal](https://paypal.me/amirstin)

Every bit helps keep this — and my other free extensions — maintained and free for everyone. Thank you!

## License

[MIT](LICENSE)
