# Prerequisites

## VR hardware requirements

* [Oculus Rift (consumer version 1.0)](https://www3.oculus.com/rift/)

If you have an [Oculus Rift Development Kit 2](https://www3.oculus.com/dk2/) (DK2), you may still be able to follow these same instructions to use WebVR, but there are no guarantees of stability nor performance.

The [Oculus Remote](https://support.oculus.com/835449819935261) is supported by the [Gamepad API (Extensions)](https://w3c.github.io/gamepad/extensions.html) in [these experimental Chromium WebVR builds](#instructions-1). Support for the upcoming hand-tracked [Oculus Touch](https://www3.oculus.com/touch/) motion controllers will be added soon once the product is released on the consumer market.

## Platform requirements

* Video Card: [NVIDIA GTX 970](http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-970) / [AMD R9 290](http://www.amd.com/en-us/products/graphics/desktop/r9) equivalent or greater.
* CPU: Intel i5-4590 equivalent or greater.
* Memory: 8GB+ RAM
* Video-compatible HDMI 1.3 video output.
* USB Ports: three USB 3.0 ports plus one USB 2.0 port.
* OS: [Windows 7 SP1](https://support.microsoft.com/en-us/help/15090/windows-7-install-service-pack-1-sp1) (64-bit) or newer.

You may wish to upgrade your Windows PC manually, order/build a new custom machine, or purchase a [prebuilt Oculus-ready PC](https://www3.oculus.com/oculus-ready-pcs/).

## Software requirements

* Download and install [Oculus Home](https://www3.oculus.com/setup/) (application for purchasing, downloading, and installing VR experiences and the required runtime to render experiences to the Oculus Rift).

### Enabling `Unknown Sources` setting for WebVR content

When launching WebVR from within the browser, you will be presented with an "Unknown Source" error screen that initially blocks WebVR content from being displayed:

![Error screen when viewing VR content without enabling 'Unknown Sources'](https://cloud.githubusercontent.com/assets/203725/18866890/ad9881de-8456-11e6-8589-76dce64b3935.jpg "Error screen when viewing VR content without enabling 'Unknown Sources'")

In an effort to protect users from applications that have not been reviewed by Oculus (for comfort, content, or health/safety), Oculus by default will not display content from apps obtained outside of the Oculus Home store. There are plenty of interesting experiences to try from trustworthy developers… including content from the Web!

#### Instructions

To resolve this, you will need to enable an option for "Unknown Sources" from within the Settings of the Oculus Home store application. Fortunately, you will need need to do this only once.

![Animation of steps to enable 'Unknown Sources' from the Oculus Home settings](https://cloud.githubusercontent.com/assets/203725/18866886/a8ffb9b2-8456-11e6-8829-d79f5c218764.gif "Animation of steps to enable 'Unknown Sources' from the Oculus Home settings")

1. Load the [Oculus Home](https://www3.oculus.com/setup/) application.
2. Located in the top-right corner, hover over the `Settings` gear icon.
3. Click the `Settings` link.
4. Ensure the `General` tab of the `Settings` is selected.
5. Click the toggle checkbox icon for `Unknown Sources` to enable it.
6. Once prompted with a dialog called `Allow Unknown Sources?`, click the `Allow` button.
7. Once the dialog is dismissed, the toggle for `Unknown Sources` should have a checkmark, indicating "unknown sources" are now allowed.
8. Now, you can freely experience WebVR content, without needing to follow this process again (even if you log in to another PC with your same user account).

# Instructions

1. Download the [latest experimental Windows Chromium build (64-bit only)](https://webvr.info/get-chrome/) by [Brandon Jones](https://twitter.com/tojiro) (WebVR Platform Engineer, Google Chrome).
2. In the URL bar, enter `chrome://flags#enable-webvr` and select `Enabled` from the drop-down menu for the `Enable WebVR` flag setting.
3. In the URL bar, enter `chrome://flags#enable-gamepad-extensions` and select `Enabled` from the drop-down menu for the `Enable Gamepad Extensions` flag setting. (As an extension to the browser's [Gamepad API](https://w3c.github.io/gamepad/), [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html) are specifically required to enable support for motion-tracked VR controllers, vibration/rumble support and haptics, touchpad detection, etc.)
3. Go enjoy some WebVR content!

<hr>

# Related links

* [[Chromium Release Notes|Release-Notes:-Chromium]]
* [[Chromium Developer Notes|Developer-Notes:-Chromium]]
