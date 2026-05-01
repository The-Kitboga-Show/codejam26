# Kitboga Code Jam 2026
"Unskippable ad"

This GitHub repository contains a template you should fork, modify to include your submission, and then submit to us. Please read all the information in this readme before getting started!
**The deadline for submissions is ~~Thursday, April 30th at 11:59 PM Eastern Time~~ Wednesday, May 6th at 11:59pm ET.**

## Rules
1. Read through the [Rules & Guidelines](https://kitboga.com/codejam26/rules)
2. Follow the guidelines in `submission/submission.html` as to where and how your code should be written.
3. No obfuscation. If we can't read or understand the code, we're probably not going to run it.
4. No requests for resources outside of your repository, except for well-known javascript libraries from a CDN (jsdelivr, unpkg, googleapis, etc). Aside from these, include all the assets you need in your repository, such as fonts, icons and everything else. If you have a specific idea which requires access to the Internet, perhaps to fetch live stock market data for example, then try to fake it. If it's important to you to make external requests, talk to us about it in Discord.
5. WebAssembly and Web Workers are not allowed.
6. Do not include minified code; this includes code generated from build tools like Vite (see also [disabling minification](https://vite.dev/config/build-options#build-minify)) or WebPack. Prefer not using any build tools, if possible.
7. Desktop browser functionality is required; mobile-friendly is preferred, but not required. Your submission will be displayed in an iframe that scales up and down while maintaining its aspect ratio — sides will not get cut off. You can rely on the iframe boundaries (e.g. `position: absolute; right: 0;` will always be the rightmost border of the video). Test for smooth functionality on desktop browser (especially Chrome/Edge) setups, and optionally also test for mobile-friendliness. (See also [device mode on Chrome](https://developer.chrome.com/docs/devtools/device-mode/), or [responsive design mode on Firefox](https://firefox-source-docs.mozilla.org/devtools-user/responsive_design_mode/).)


## Discord
Please feel free to join the Kitboga discord, and hang out in the [#code-jam](https://discord.com/channels/331609590229893120/1377638134917103647) channel. That's a great place to ask for help, and it will be useful if we need to contact you about your submission for whatever reason.
https://discord.com/kitboga

## Getting Started
1. Create a GitHub repository from the template: https://github.com/new?template_name=codejam26&template_owner=The-Kitboga-Show
2. Clone the new repository locally to your machine
3. Open the "game shell" in your browser; this can be done in 2 ways:
   - By opening `index.html` directly in your browser
   - By running a local webserver (this can help with testing on different devices too). One easy way to do this, if you have python installed, is to run this command in the terminal: `python3 -m http.server 8000`. Then open [http://127.0.0.1:8000](http://127.0.0.1:8000) in your browser (the port may vary if you used a different method to start a web server).
4. Create your game in `submission/submission.html`! All parts of your submission should be in the `submission/` folder.
5. Commit and push your changes
6. See the "How to Submit" section below

## Forbidden APIs and functions
Please don't use any of the following:
- navigator.geolocation
- navigator.getUserMedia()
- navigator.connection
- navigator.clipboard
- navigator.bluetooth
- navigator.usb
- navigator.serial
- navigator.requestMIDIAccess
- window.showOpenFilePicker()
- window.showSaveFilePicker()
- navigator.serviceWorker
- window.open()
- window.print()
- navigator.permissions
- navigator.credentials
- RTCPeerConnection
- fetch, XMLHttpRequest, WebSocket, etc.

## Examples
The `examples/` folder contains several example submissions for inspiration:
- **Buffering** (`examples/buffering/`) — Simulates frequent video buffering that pauses and resumes playback
- **Fake X** (`examples/fake-x/`) — A fake close button that restarts the ad; the real skip link is somewhere else
- **Slowdown** (`examples/slowdown/`) — A "Skip in 3...2...1" countdown where each second takes exponentially longer
- **Survey** (`examples/survey/`) — A post-ad star rating survey that randomly rejects your answer

Use the dropdown in the dev shell to load and test each example.


## Prizes and Judging
Entries will go through a series of progressive rounds of review/judging. They will first be shortlisted by a panel of Kitboga team members based on cleverness, technical skill, hookability, style and humor. See the [main webpage](https://kitboga.com/codejam26) for more clarity on these criteria.

The best submissions will go on to be showcased and reviewed on-stream by Kitboga & Twitch Chat via polling, and the best of those submissions will be tested with scammers.

Prizes will include merch; Amazon Prime, Twitch & Kraken+ subscriptions; Discord emoticons and roles; and more!

## How to submit
**Remember, the deadline is ~~Thursday, April 30th at 11:59 PM Eastern Time~~ Wednesday, May 6th at 11:59pm ET!**
Don't forget to [read the license](https://kitboga.com/codejam26/terms), which you'll need to agree to in order to take part.

Go here: https://kitboga.com/codejam26

## (Optional) Live Demo
Add a publicly viewable demo for your submission by enabling GitHub Pages in your repository settings. Navigate to `Settings` > `Pages`, then under `Branch`, select `main`, and then press `Save`. Once the site is built the URL will appear.

## FAQ

**We can use requestAnimationFrame, correct?**
Yes. Anything but the listed functions under "Forbidden APIs and functions" is allowed.

**Are the ads in the same structure in the live demo? As in, located in ../ads and named something like ad_12.mp4**
That's just an example which you can use to test your code. You won't know the name or location of the actual videos, but you can get limited info using a `getVideoInfo` request.

**Is the iframe always bound to the confines of the video? Can I rely on `position: absolute; right: 0;` always being the rightmost border of the video?**
Yes to both. We will force it to be one size, even if it is a bit on the small side for the container, so you have a consistent size to work from.

**Will the actual video during the live demo be responsive? As in — will it change sizes, or just get the sides cut off, e.g. on mobile?**
It will scale up and down, maintaining the aspect ratio — sides will not get cut off.

**How do I edit/delete a submission?**
If you haven't finalized it, you can edit the repo or delete the entry at any time.

Once you've finalized your submission, we pull a copy of your repo, and you can no longer update or delete it on your end.

If you realize there's a bug or want to make edits or updates, you can always work on a new release and submit as a new entry. *Title it the same name as the previous, and put something like [New v3.27 - delete old] after the title - so we know which one is the new one, and makes it easier for us to delete old one*. Then DM Michael or put a message in #code-jam to let us know you submitted a replacement and to delete the old one.

Since we need to manually find and delete these, please do this as a last resort.  You don't need to finalize your submission until you've done all the testing you want and you feel like it's ready to ship :) 

## Further help
Drop into the Kitboga discord server, and check out the [#code-jam](https://discord.com/channels/331609590229893120/1377638134917103647) channel. Please don't ask questions via email, as we might not see them before the deadline.

## API

All communication between your submission and the game shell uses `window.top.postMessage()`. Messages use the format `{ type: string, value?: any }`.

### Sending events (submission -> shell)

| Message                                      | Description                                                                     |
|----------------------------------------------|---------------------------------------------------------------------------------|
| `{ type: 'success' }`                        | The ad was successfully dismissed. Shows a success banner and reloads the page. |
| `{ type: 'fail' }`                           | The user failed the ad. Shows a fail banner and reloads the page.               |
| `{ type: 'play' }`                           | Resume video playback.                                                          |
| `{ type: 'pause' }`                          | Pause video playback.                                                           |
| `{ type: 'seekTo', value: number }`          | Seek the video to a specific time (in seconds).                                 |
| `{ type: 'setPlaybackRate', value: number }` | Set the video playback rate (e.g. `0.5` for half speed, `2` for double).        |
| `{ type: 'setVolume', value: number }`       | Set the video volume (`0` to `1`).                                              |
| `{ type: 'getVideoInfo' }`                   | Request current video state. The shell responds with a `videoInfo` event.       |
| `{ type: 'setVideoFilter', value: string }`  | Apply a CSS filter to the video (e.g. `'blur(2px)'`, `'hue-rotate(90deg)'`).    |

Example:
```js
// Dismiss the ad
window.top.postMessage({ type: 'success' }, '*');

// Slow down the video
window.top.postMessage({ type: 'setPlaybackRate', value: 0.25 }, '*');

// Apply visual effects to the video
window.top.postMessage({ type: 'setVideoFilter', value: 'blur(2px)' }, '*');
window.top.postMessage({ type: 'setVideoFilter', value: 'hue-rotate(90deg) saturate(1.5)' }, '*');

// Clear video filter
window.top.postMessage({ type: 'setVideoFilter', value: 'none' }, '*');

// Request current video timing info
window.top.postMessage({ type: 'getVideoInfo' }, '*');
```

### Receiving events (shell -> submission)

Listen for events from the shell using `window.addEventListener('message', ...)`.

| Message                  | Description                                                                      |
|--------------------------|----------------------------------------------------------------------------------|
| `{ type: 'adStarted' }`  | The ad has started. Sent when the video begins playing and the iframe is loaded. |
| `{ type: 'adFinished' }` | The video has finished playing (reached the end).                                |
| `{ type: 'timeupdate', currentTime, duration, paused, playbackRate }` | Sent periodically during playback with current video timing info. |
| `{ type: 'videoInfo', currentTime, duration, paused, playbackRate, volume, muted }` | Response to a `getVideoInfo` request. |

Example:
```js
window.addEventListener('message', (event) => {
  if (!event.data || !event.data.type) return;

  switch (event.data.type) {
    case 'adStarted':
      // The ad has started, show your overlay
      break;
    case 'adFinished':
      // The video ended, e.g. show a survey or call fail
      break;
    case 'timeupdate':
      // Called frequently during playback
      const { currentTime, duration } = event.data;
      const timeRemaining = duration - currentTime;

      // Example: Do something 10 seconds before the video ends
      if (timeRemaining <= 10 && timeRemaining > 9) {
        console.log('10 seconds left!');
      }
      break;
    case 'videoInfo':
      // Response to getVideoInfo request
      console.log('Video info:', event.data);
      break;
  }
});

// Request video info on demand
window.top.postMessage({ type: 'getVideoInfo' }, '*');

// Apply a CSS filter to the video
window.top.postMessage({ type: 'setVideoFilter', value: 'hue-rotate(20deg)' }, '*');
```

### Default behavior

The submission template listens for `adFinished` and calls `fail` by default — if the user doesn't skip the ad before the video ends, it is marked as a fail. You can replace this with any other interaction (see `examples/survey`), but your submission must eventually call success or fail.
