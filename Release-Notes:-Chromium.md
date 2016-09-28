# Changelog

**WARNING:** All [Chromium WebVR builds posted here](https://webvr.info/get-chrome/) are experimental! They have not been vetted by Google, [me (Brandon Jones)](https://twitter.com/tojiro), nor anyone else for security or stability, and under no circumstances should you use them as your day-to-day browser! They are provided for testing of the experimental WebVR APIs only.

Please report Chromium WebVR bugs to [https://github.com/toji/chrome-webvr-issues/issues](https://github.com/toji/chrome-webvr-issues/issues).

To discuss WebVR or request features, please join the [`public-webvr` mailing list](https://lists.w3.org/Archives/Public/public-webvr/) or participate in the [WebVR API spec on GitHub](https://github.com/w3c/webvr/issues).

### September 23, 2016

* `vrdisplayactivate` events are now user gestures that can trigger `VRDisplay.requestPresent`.
* Updated how `VRLayer` bounds are handled to match the latest spec updates.
* Fixed issue where repeated calls to `VRDisplay.requestPresent` after the display was already presenting failed without a user gesture (e.g, `click`, `touch`, etc.).
* Those fixes enable the newest [WebVR sample](https://webvr.info/samples/), which shows how to adjust the output resolution on the fly without resizing the canvas (which is expensive).

### September 17, 2016

* Big update!
* Updated API to the [WebVR “1.1” spec](https://w3c.github.io/webvr/). Almost all older content should continue working, but is now considered deprecated. Please take a moment to [update your code](https://github.com/w3c/webvr/blob/gh-pages/migration.md)!
* `VRDisplay.requestPresent` **must happen in a user gesture** (e.g, `click`, `touch`, etc.).
  * This will probably screw with some people’s code. Please reach out to me if it causes you problems! The requirement isn’t going away, but I want to ensure that all reasonable use cases have a way to work within it.
* To better stay in sync with ToT Chrome, the [VR-centric gamepad APIs](https://w3c.github.io/gamepad/extensions.html) (Pose, Hand, Haptics) are now behind the “Gamepad Extensions” flag in `chrome://flags`. I know it sucks to have to flip more switches, but this is the cleanest way for me to move forward.
* To stay in sync with the [Gamepad Extensions spec](https://w3c.github.io/gamepad/extensions.html), the gamepad haptics API has changed:
  * `gamepad.haptics` is now `gamepad.hapticActuators`.
  * `vibrate()` is now `pulse()`.
* Lots and lots of behind-the-scenes madness while we work on landing WebVR in the browser proper. Much of it shouldn’t be visible, but there’s always the chance that shifting things around breaks something. [File bugs](https://github.com/toji/chrome-webvr-issues/issues) when you find them!
* The HTTP warning (for non-HTTPS sites) is not in this build, but expect it soon.

### August 29, 2016

* Made sure that this build was zipped in such a way that the normal Windows unzip could handle it.
* Added `VRDisplay.depthNear` and `VRDisplay.depthFar`, which I had neglected to add previously even though they were in the spec.
* Made a couple of other minor tweaks. Doubt anyone will notice.

### August 28, 2016

* Desktop updates are slow because development has been full speed ahead on Android recently! Hoping fuller WebVR implementations will end up in the Chrome Dev channel on Android soon.
* Lots of WebVR code being merged into Chrome proper at this point. Experimental branch is shrinking!
* Haptics are back! New API, based on [API proposal](https://github.com/w3c/gamepad/issues/19) from [@cvan](https://twitter.com/cvanw). Briefly:
  * `gamepad.haptics` is an array of motors.
  * Each `GamepadHaptics` object in the array has a `vibrate()` function.
  * `vibrate()` takes an `intensity` from 0 to 1 and `duration` in ms (as a double float; sub-ms input is allowed).
  * XInput devices have two elements in the array; Vive wands have one.
  * See [VR controllers](https://toji.github.io/webvr-samples/XX-vr-controllers.html) sample ([source](https://github.com/toji/webvr-samples/blob/gh-pages/XX-vr-controllers.html)) for example usage.
* There are some known bugs with the haptics code. For example: duration of individual motors can interfere with one another. Should still be enough to start testing.

### August 7, 2016

* Fixed bug with OpenVR events that were preventing them from firing in some cases. (Fixes IPD not updating when spinning the dial, for example.)
* Fixed erroneous `pose` showing up on gamepads with no pose (e.g., Xbox controllers).
* Moved `hasOrientation` and `hasPosition` to `GamepadPose` rather than `GamepadCapabilities` (now removed). This is to keep in line with the latest spec proposals.
* Added `hand` attribute to gamepads, after a proposed addition I made to the spec. Set `""` to for gamepads that are held with both hands or where the hand is unknown. Set to `"left"` or `"right"` when the controller has a known associated hand. For the Vive this can change dynamically. I expect that it will be static for Oculus Touch, since the controllers are each made for a specific hand.

### July 29, 2016

* Updated even names to be consistent with the versions that made it into the spec. They’re all present tense now:
  * `vrdisplayactivated` → `vrdisplayactivate`
  * `vrdisplaydeactivated` → `vrdisplaydeactivate`
  * `vrdisplayconnected` → `vrdisplayconnect`
  * `vrdisplaydisconnected` → `vrdisplaydisconnect`
* Added `vrdisplayblur` and `vrdisplayfocus` events for when you call up the platform dashboard/menu over the top of WebVR content, but not convinced they’re working the way they should. Gonna experiment some more before proposing in the spec.
* Updated OpenVR SDK to 1.0.2.

### July 19, 2016

* Fixed issue with Oculus headsets presenting WebGL 2.0 content.
* Events fire without polling now, though there’s still some cases where they don’t work like you’d want them to.
* `vrdisplayactivated` and `vrdisplaydeactivated` don’t fire at intuitive times with the Vive. Not sure why. :(
* Lots of internal plumbing that’s being re-routed for the event handling. Hopefully it doesn’t actually have much visible effects.

### July 10, 2016

* Exposed `vrdisplayactivated`, `vrdisplaydeactivated`, and `vrdisplaydisconnected` events.
  * Known issue: Only fires when the pose is actively being polled.
  * Known issue: `vrdisplaydeactivated` won’t fire on Vive right now because of an implementation bug.
* Technically, `vrdisplayconnected` is also able to fire, but since it only fires when polling the display pose and the display has to already have been detected to poll the pose it doesn’t do any good.
* FYI: The event names may be tweaked slightly in the future to be present tense (i.e., `vrdisplayactivated` → `vrdisplayactivate`). Follow [https://github.com/w3c/webvr/pull/59](https://github.com/w3c/webvr/pull/59) for details.

### July 6, 2016 (Take 2!)

* _Actually really truly_ for reals this time I promise I fixed the issue with Oculus Rift re-centered upon repeat calls to `requestPresent`.

### July 6, 2016

* **Actually** fixed issue with the Oculus Rift re-centered upon repeat calls to `requestPresent`.
* Added `--force-openvr` flag that forces Oculus devices to use OpenVR instead of the Oculus SDK.
  * In my experience, this is a bit more juddery, but _may_ allow Oculus Touch to be exposed. Also useful for debugging.

### June 30, 2016

* Fixed issue with the Oculus Rift re-centered upon repeat calls to `requestPresent`.
* On Vive changes to headset configuration like IPD and StageParameters are now actively pushed to the VRDisplay, so your application can respond to them in real time! Still need to wire this up for the Rift.

### June 29, 2016

* Just a re-packaging of yesterday’s build to make sure a missing file was included.
* `.zip` this time, because I guess nobody likes 7z? File is 50% bigger as a result.

### June 28, 2016

* Primarily getting back to full functionality after some large internal refactoring.
* Updated to Oculus SDK 1.5.0.
* Gamepad API additions are closer now to how I hope their final versions will look.
  * Now includes `gamepad.capabilities`.
  * Using a `GamepadPose` object now rather than re-using `VRPose`. Lacks timestamp.
  * `touched` button attribute now set to `true` any time pressed is `true`.
  * Removed vibration functions, since I don’t think it will ever ship in the form it was in.
* Vive gamepads now report linear and angular velocity.
* Added new command line flag for development: `--emulate-daydream-webvr`.
  * This flag will never see a real build, it’s mostly for my own development needs.
  * When this flag is set a Vive will appear to WebVR with capabilities similar to a Daydream headset/controller for testing and prototyping purposes.
  * Headset is restricted to 3DoF.
  * Controller is restricted to 3DoF.
  * Only one controller is exposed.
  * Controller only exposes touchpad and application button.

### May 21, 2016

* Will be publishing only 64-bit Windows builds from now on to address memory issues with some asm.js apps. I can’t imagine there’s many VR-capable systems at this point that aren’t running a 64-bit OS.
* Not a whole lot of visible changes, mostly just slowly merging bits of code into top-of-tree Chromium. Which is a good thing, because it means we’re inching closer to actually launching this thing.
* Fixed a problem where presentation wasn’t properly shutting down till you closed the tab. This meant that Rifts would continue showing a frozen frame and Vive’s would report “Unresponsive” in the VR status monitor. Now they should both cleanly stop presenting and either go dark or back to their respective home screens.

### April 24, 2016

* Now supports Vibration on XInput devices and Vive controllers!
  * Support is VERY experimental. Vibration interface may change at any point!
* Refactored how touchpads are supported in Gamepad API.
  * Buttons now include a `touched` boolean alongside `pressed` and `value`.
  * This has caused the buttons on the Vive to shift a bit. Touchpad is now only button 0 and trigger is button 1. Update your code accordingly.
  * Again, very experimental! May disappear or be refactored in the future.
* Stopped the Oculus Rift from exposing itself as two gamepads.
  * What is this? I don’t even…
* Fixed crash when Vive lost tracking while presenting.
* Fixed crash when calling `requestPresent` without calling `getPose` first.
  * Turns out those two were the same crash!

### April 18, 2016

* Now providing a single build that supports both the Oculus and OpenVR SDKs!
  * SHOULD theoretically support both at the same time. I don’t have enough ports to test that out.
  * Even if that does work can currently only present to one HMD at a time.

### April 6, 2016

* Oculus-only release.
* Exposes the Oculus Remote via the Gamepad API.

### April 2, 2016

* OpenVR-only release.
* Updated to support the latest spec revisions.
  * `requestPresent` accepts an array of `VRLayer`s.
  * `capabilities.maxLayers` reports how many layers can be passed (locked to 1).
* Updated gamepad polling rate to make Vive controller motion smoother.
* Still hitches, but far less juddery than before.
* Some changes to the OpenVR presentation pipeline that I doubt anyone will actually notice.

### March 29, 2016

* Oculus-only release.
* Updated to the 1.3.0 SDK.
* **IMPORTANT:** In order to use this build, you MUST [allow Unknown Sources in Oculus Home.](https://support.oculus.com/878170922281071)

### March 24, 2016

* OpenVR-only release.
* Fixed frequent crash from previous build.
* Updated OpenVR SDK to 0.9.19.

### March 22, 2016

* OpenVR-only release.
* Vive controller support! Exposed via the Gamepad API, which has an optional `pose` attribute on it in this build.
* WARNING: The new additions to the Gamepad API in this build are completely experimental and may not ever make it into the Gamepad spec! Feel free to play with it, but don't get too dependent on it in its current form.

### March 20, 2016

* Fixed Vsync being turned off by default! Still runs at correct framerate for headset when presenting.
* Fixed issue with submit frame pipeline, now allows for advanced mirroring techniques. (See [https://toji.github.io/webvr-samples/07-advanced-mirroring.html](https://toji.github.io/webvr-samples/07-advanced-mirroring.html) for an example.)

### March 7, 2016

* Fixed a major source of crashes. Seems much more stable now.

### March 6, 2016

* Fixed issue with calling resetPose with the Oculus build that was causing scene to show up as a “window” off to one side of your view.
  * As an unfortunate side effect of this fix, the Oculus build resets your pose when you call `requestPresent`.
* Implemented support for `VRLayer.leftBounds` and `VRLayer.rightBounds` in Oculus and OpenVR builds.
* Tried to fix issues with VR compositing shutting down properly when you navigate away from a page. Not sure how much better it is, though.

### February 21, 2016

* Major API update! Now implements the first draft of the “WebVR 1.0” API.
* Not backwards compatible with previous builds!
* Many of the same presentation caveats still apply:
  * Forced OpenGL.
  * Forced Vsync off.
  * etc.

* Some known issues related to the new API:
  * Connect/disconnect events are not implemented and `isConnected` always reports `true`.
  * `submitFrame` doesn’t clear the canvas like it should when not using `preserveDrawingBuffer`.
  * `stageParameters` don’t properly update when `resetPose` is called.
  * IPD and field of view don’t update after the headset is queried.
  * If you don’t explicitly exit VR present before navigating away from a page, it can get unstable.
* `VRDisplay.requestPresent` is not restricted to being called during user gestures, but likely will be in the future.

### November 25, 2015

* Oculus update.
* Fixed issue with scenes being over-bright in the HMD.
  * SDK was interpreting images as SRGB when they weren’t.
* Re-added Timewarp: Smoothest. WebVR. Evar!

### October 30, 2015

* Re-release of Oculus 0.8.0.0 SDK Build.
* Fixed issue with inverted IPD in previous build.

### October 23, 2015

* Built against Oculus 0.8.0.0 SDK.
* Windows only. (Again, not something I have control over.)
  * On the plus side, Windows 10 now supported!
* Many of the same caveats as the OpenVR build:
  * Forces rendering with OpenGL.
  * Forces Vsync off (will cap at 90Hz when in VR mode).
  * Forces “basic” theme, so no transparent title bar in Win 7.
  * Forces the GPU sandbox off. Badly behaved WebGL apps may crash the browser.
  * May be juddery.
* Timewarp has been disabled. Should be able to fix that soon.
* Scenes may appear overly bright. I think I need to tweak some SRGB setting.

### October 12, 2015

* First public OpenVR build (HTC Vive support)!
* Windows only. (Not my choice, folks!)
* OpenVR build has some quirks when WebVR is enabled that you should be aware of:
  * Does NOT support the Oculus Rift. Input may work, rendering is broken.
  * Forces rendering with OpenGL.
  * Forces Vsync off (will cap at 90Hz when in VR mode).
  * Forces “basic” theme, so no transparent title bar in Win 7.
  * Forces the GPU sandbox off. Badly behaved WebGL apps may crash the browser.
  * Will probably still judder a bit. Seems to depend on the page.
* No Vive controller support at this point, sorry!
* This build _should_ trigger the OpenVR compositor if run by itself, but I’ve found that I get the most reliable performance when running the SteamVR status app in the background.
* Renamed all the other builds, which tweaked their upload date. Sorry, nothing new to see there!

### Aug 21, 2015

* Project Tango-enabled build!
* No HMD information returned in the Tango build, it’s intended to be used while holding the tablet. Might change that later for use with Durovis Dive and friends.

### May 24, 2015

* Android update
* Using newly available Chrome Public build target (effectively Chromium for Android).
  * Crucially, this provides much, MUCH better fullscreen behavior.
* Distortion has regressed in this build, sorry. There were several known cases where it was causing more harm than good, though. Working on getting it to work more reliably for a wide range of harnesses.

### April 26, 2015

* Desktop update.
* Restored Oculus Extended Desktop support on Windows, Mac, and Linux.

### April 21, 2015

* Android-only update.
* Updated to the Cardboard 0.5.3 SD.
* Several large “under-the-hood” changes that should have no visible effect aside from hopefully improving stability.

### March 28, 2015

* Windows only update.
* Backwards-incompatible API changes! Updated to match recently published [WebVR Spec](https://mozvr.github.io/webvr-spec/webvr.html).
  * Most HMD queries have been replaced with a single call: `getEyeParameters(VREye whichEye);`.
* Updated to Oculus 0.5.0.1 SDK.
* **Need to enable WebVR support** by navigating to `chrome://flags` and clicking the “Enable” link under the “Enable WebVR” section.
* **This release does not support extended desktop mode!**
  * This is unrelated to the Oculus SDK update, it’s a side effect of recent Chrome changes.
* Still supports Direct-to-HMD mode.
* Should be significantly less crash-y.

### March 26, 2015

* Long time between updates! Sorry!
* Android only update for the moment.
  * _Backwards-incompatible API changes!_ Updated to match recently published [WebVR Spec](https://mozvr.github.io/webvr-spec/webvr.html).
  * Most HMD queries have been replaced with a single call: `getEyeParameters(VREye whichEye);`.
* **Need to enable WebVR support** by navigating to `chrome://flags` and clicking the “Enable” link under the “Enable WebVR” section.
* Updated to use the Cardboard 0.5.2 SDK.
* Lots and lots and lots of internal refactoring that probably won’t be visible to the rest of the world.

### December 30, 2014

* Provides `HMDVRDevice` on Android now.
  * Pulls data from the Cardboard API.
* Allows VR Fullscreen with distortion on Android.
  * Seems to work better on some devices than others.
  * May crash.
  * No timewarp yet.
* Removed `getTimewarp()` and `setTimewarp()` from `HMDVRDevice`.
  * Now you pass it in as a fullscreen option: `{vrTimewarp: true}` or `{vrTimewarp: false}`.
* Direct-to-HMD should work with non-distorted fullscreen now.

### December 17, 2014

* Windows-only release
* Enables Direct-to-HMD mode!
  * Known issue: Does not yet work with fullscreen option `{vrDistortion: false}`.
  * Known issue: Occasionally, I get a modal error dialog about the Rift being initialized on different GPU than it’s connected to (which is not actually the case). This error doesn’t prevent Direct-to-HMD mode from working, though, as long as you click through it. No idea what this is about.
* Extended mode is still available. Automatically selected based on your Rift configuration.

### December 5, 2014

* Rebuild with the 0.4.4 SDK.
* Fixed garbage data outside the visible area when in VR fullscreen.

### November 18, 2014

* Fixed another variant of the timewarp bug that was likely to affect [three.js samples](https://threejs.org/examples/).
* `requestFullscreen` with `vrDisplay` can now be called on any element, but will still only take effect on WebGL canvases beneath that element. (Doesn’t work for `<iframe>`s.)
  * This partially fixes the missing distortion effects on [MozVR.com](https://mozvr.com/), but the main content is still undistorted.
* Stopped clearing when rendering a VR canvas. Started taking canvas alpha into consideration.
  * Allows layered effects (like on [MozVR.com](https://mozvr.com/)).
  * Chromatic aberration compensation means alpha channel is subtly wrong.
  * Means you get garbage outside the rendered area, shouldn’t be visible in the HMD if your profile is correctly configured.
  * Will probably find a way to make the garbage go away at some point, if only because it looks better when mirrored.
* Added `getTimewarp()` to `HMDVRDevice` so you can tell if timewarp is being applied.
  * Similar to `setTimewarp`, this is primarily for debugging and may disappear later.
* A few more minor bug fixes that I doubt anyone will notice.

### November 14, 2014

* Fixed terrible timewarp bug that made the previous builds essentially unusable. Oops.

### November 13, 2014

* Rebuilt with the 0.4.3 SDK.
  * Yes, this means you get more vignetting. Oculus will fix it in an upcoming SDK.
* I am _attempting_ <span>to provide a Linux build this time around. Be advised that I will offer basically zero support if you can’t get it running because I am decidedly NOT a Linux guru.
* Significant refactoring of how distortion rendering works.
* New architecture allows for timewarp!
  * Timewarp is enabled by default.
  * New, possibly temporary, debugging function added to `HMDVRDevice`: `setTimewarp(bool);`.
* `setFieldOfView` is known to be broken in this build.
  * You can set the value and `getRecommendedEyeRenderRect` still responds properly, but it won’t affect the distortion rendering.
* Like in the previous Android build, `VRPositionState` members which are not populated will be `null` now, instead of zeroed out.

### November 6, 2014

* Early release of WebVR-enabled ChromeShell for Android.
* Uses [Cardboard SDK](https://developers.google.com/vr/concepts/overview-cardboard).
* Only supports orientation tracking in this release, no `HMDDevice` will be returned.
* `VRPositionState` members which are not populated will be null now, instead of zeroed out.
* Immersive Fullscreen is not available in ChromeShell builds, so the status bar and home buttons stay on screen. Sorry!

### October 12 & 13, 2014

* This release is primarily to catch WebVR builds up to Top-of-Tree Chromium.
* Refactored how fullscreen works internally, no user-facing improvements as a result of this change. (Sorry!)

### September 11, 2014

* Rebuilt with the 0.4.2 SDK.
* Inverted values returned from `getEyeTranslation`. Firefox will also be making this change. It will break existing content, but we agreed that the new value is more intuitive for the general case. (For example, in [three.js](https://threejs.org) you now add these values to the camera position instead of subtracting them.)
* Changed `PositionSensorVRDevice` function `resetSensor` to `zeroSensor` for Firefox compatibility.
* Removed `getRecommendedRenderTargetSize` in favor of `getRecommendedEyeRenderRect(whichEye)` for Firefox compatibility. The values returned are what should be passed to `gl.viewport` when rendering each eye. Render target size can be calculated like so:

  ```js
  var leftEyeRect = hmd.getRecommendedEyeRenderRect("left");
  var rightEyeRect = hmd.getRecommendedEyeRenderRect("right");
  var width = leftEyeRect.width + rightEyeRect.width;
  var height = Math.max(leftEyeRect.height, rightEyeRect.height);
  ```

### August 14, 2014

* Rebuilt with the 0.4.1 SDK.
* Mac support is back!
* Same caveats as previous builds.

### August 8, 2014

* Rebuilt with the 0.4.0 SDK, now supports DK2! (Windows only due to limited SDK support)
* Only supports Extended desktop mode currently.
* Chrome’s animation pipeline still runs at 60Hz instead of the native DK2 refresh rate of 75Hz.
* You will probably get some judder.

### July 17, 2014

* Added `getCurrentEyeFieldOfView`, `getMaximumEyeFieldOfView`, and `setFieldOfView` to `HMDVRDevice` interface to match Firefox API.
* Removed `renderTargetSize` attribute from `HMDVRDevice` and added `getRecommendedRenderTargetSize` function. Returned value changes when the Field of View is changed.
* Removed `displaySize` attribute from `HMDVRDevice`. I can’t see any useful way to use it in JavaScript.

### July 7, 2014

* Going into Fullscreen VR mode now automatically displays content on the HMD without mirroring. Currently the entire browser moves over to the HMD display, then moves back when you escape out of fullscreen mode. This is a temporary hack to make testing VR content easier. The intention is that only the VR content will be sent to the HMD while the rest of the browser content is left in place, most likely with a placeholder element where the VR content’s element used to be.

### July 3, 2014

* Fixed issue when applying VR distortion to some WebGL content, specifically [three.js scenes](https://threejs.org/examples/).

### July 2, 2014

* [Initial experimental builds made available.](http://blog.tojicode.com/2014/07/bringing-vr-to-chrome.html)
