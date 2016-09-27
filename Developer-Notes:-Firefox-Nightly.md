# Windows

## What is Firefox Nightly vs. Firefox?

It's worth noting that WebVR for [Firefox](https://www.mozilla.org/firefox/) is being developed in the [open-source codebase](https://hg.mozilla.org/mozilla-central/) of the main Firefox browser that gets released to users. Early access to snapshots of the experimental state of Firefox is available for download as the [Firefox Nightly browser](https://nightly.mozilla.org/). This that the codebase for Firefox is open source, and the browser functions as you would normally expect in release channel Firefox: automatic updates, full codec support, and your expected JavaScript APIs are all still available to you in Firefox Nightly. (See the [[Developer Notes for Firefox Nightly|Developer-Notes:-Firefox-Nightly]].)

# Mac OS X

_Currently unsupported by Oculus._

# Linux

_Currently unsupported by Oculus._

# Android

[Firefox for Android](https://www.mozilla.org/firefox/android/) currently supports an out-of-date version of the [WebVR API](https://w3c.github.io/webvr/) (pre-[v1.0](https://hacks.mozilla.org/2016/03/introducing-the-webvr-1-0-api-proposal/)). Mobile support is currently deprioritized in order to first achieve a stable, performant WebVR browsing experience on desktop (which is limited to Windows only for desktop because of restrictions enforced by VR headset makers until the performance of Mac and Linux improves, as improved processors and graphics cards become readily available on the market).

# iOS

[Firefox for iOS](https://www.mozilla.org/firefox/ios/) (as are [Google Chrome for iOS](https://developer.chrome.com/multidevice/ios/overview) and [Apple's Safari browser for iOS](https://en.wikipedia.org/wiki/Safari_(web_browser)) is built atop the [WebKit browser](https://webkit.org/). As Apple permits only Safari to access privileged iOS utilities (e.g., the iOS Nitro engine), Firefox/Chrome for iOS use Apple's [`UIWebView`](https://developer.apple.com/reference/uikit/uiwebview) for loading and rendering content.

Because WebVR support is not available in WebKit, native WebVR support is currently unavailable in every browser on the iOS platform. A limited subset of the capabilities of the WebVR API, however, can be emulated for iOS browsers using [this WebVR Polyfill](https://github.com/borismus/webvr-polyfill) (which makes use of the phone's sensors to simulate a [Cardboard](https://vr.google.com/cardboard/)-like headset).

<hr>

# Related links

* [[Chromium Release Notes|Release-Notes:-Chromium]]
