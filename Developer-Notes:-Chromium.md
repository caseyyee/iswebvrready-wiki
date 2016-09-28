# Windows

## Downloads / Instructions

* **[Download experimental Chromium builds for Windows.](https://webvr.info/get-chrome/)**
* **[[Read instructions for Oculus Rift.|Instructions:-Chromium-for-Oculus-Rift-on-Windows]]**
* **[[Read instructions for HTC Vive.|Instructions:-Chromium-for-HTC-Vive-on-Windows]]**

## What is Chromium vs. Chrome?

[Chromium](https://www.chromium.org/) is the open-source project that forms the basis for [Google Chrome](https://www.google.com/chrome/). Because it's open source, there are a few limitations with using the [experimental Chromium WebVR builds](https://webvr.info/get-chrome/). Fortunately, patches are being actively uplifted in piecemeal in preparation for eventual release of WebVR in the proper Google Chrome product.

* **Automatic updates.** Unlike the Chrome/Canary release channels, you have to manually download and reinstall each new version of a Chromium build.
* **Limited codec support.** MP3 and x264, for example, are not supported because of licensing issues with Chromium, but not Chrome, being an open-source project. Codec support may vary by platform, but these codecs _are_ supported: Opus (Ogg containers), WebM, Theora, Vorbis, VP8, VP9, and WAV. (More info [here](https://www.chromium.org/audio-video) and [here](https://www.chromium.org/developers/design-documents/video), and [here](https://chromium.googlesource.com/chromium/src/+/master/docs/chromium_browser_vs_google_chrome.md#Chromium).) Workaround: use `ffmpeg` or a similar tool to convert audio and video to accepted formats.
* **Speech Recognition and Speech Synthesis APIs.** Out of the box, Chromium does not support these APIs (because they rely on [Google's Cloud Program](https://cloud.google.com/) services). If you generate [signed API keys for Chromium](https://www.chromium.org/developers/how-tos/api-keys), subscribe to the Chromium Developers mailing list (to be recognized as a developer), enroll in the [Google Cloud Program's Cloud Speech™ API](https://cloud.google.com/speech/), and enter some keys into the Cloud Speech API interface, you can unlock access (albeit limited, but to a reasonable degree) to use the aforementioned Speech JS APIs just like you normally would in Chrome/other browsers.

It's worth noting that WebVR for [Firefox](https://www.mozilla.org/firefox/) is being developed in the [open-source codebase](https://hg.mozilla.org/mozilla-central/) of the main Firefox browser that gets released to users. Early access to snapshots of the experimental state of Firefox is available for download as the [Firefox Nightly browser](https://nightly.mozilla.org/). This that the codebase for Firefox is open source, and the browser functions as you would normally expect in release channel Firefox: automatic updates, full codec support, and your expected JavaScript APIs are all still available to you in Firefox Nightly. (See the [[Developer Notes for Firefox Nightly|Developer-Notes:-Firefox-Nightly]].)

# Mac OS X

* _Currently unsupported by Oculus._

# Linux

* _Currently unsupported by Oculus._

# Android

* [[Read instructions for Chromium for Android.|Instructions:-Chromium-for-Google-Cardboard-on-Android]]
* [Download experimental builds.](https://webvr.info/get-chrome/)

# iOS

* _Currently unsupported by Apple on iOS ([[see notes on iOS|Instructions:-iOS]]).

<hr>

# Related links

* [[Chromium Release Notes|Release-Notes:-Chromium]]
