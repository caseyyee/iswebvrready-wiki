# Prerequisites

## VR hardware requirements

* [Oculus Rift (consumer version 1.0)](https://www3.oculus.com/rift/)

If you have an [Oculus Rift Development Kit 2](https://www3.oculus.com/dk2/) (DK2), you may still be able to follow these same instructions to use WebVR, but there are no guarantees of stability nor performance.

Support for the [Oculus Remote](https://support.oculus.com/835449819935261) and upcoming [Oculus Touch](https://www3.oculus.com/touch/) controllers is unavailable in the current versions of Firefox Nightly. You can follow the platform progress of the Firefox implementation of the [Gamepad API (Extensions)](https://w3c.github.io/gamepad/extensions.html) [here on IsWebVRReady.org](https://iswebvrready.org/#gamepad-extensions) (and, in particular, [this Firefox platform bug](https://bugzilla.mozilla.org/show_bug.cgi?id=1196672)). Stay tuned!

It's worth noting that the [experimental Chromium builds](https://github.com/Web-VR/iswebvrready/wiki/Instructions%3A-Chromium-for-Oculus-Rift-on-Windows) currently do support [VR motion controllers](https://iswebvrready.org/#gamepad-extensions).

## Platform requirements

* Graphics Card: [NVIDIA GeForce GTX 970](http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-970) / [AMD Radeon R9 290](http://www.amd.com/en-us/products/graphics/desktop/r9) or better.
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

1. Download the [latest Windows Firefox Nightly build (64-bit)](https://nightly.mozilla.org/) by [Kip Gilbert](https://twitter.com/kearwoodgilbert) (WebVR Platform Engineer, Mozilla Firefox).
2. Go enjoy some WebVR content!

<hr>

# Related links

* [[Firefox Release Notes|Release-Notes:-Firefox]]
* [[Firefox Developer Notes|Developer-Notes:-Firefox]]
