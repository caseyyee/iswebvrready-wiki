# Prerequisites

## VR hardware requirements

* [**HTC Vive** (consumer version 1.0) headset](https://www.vive.com/us/)
  * [Vive User Guide](http://dl4.htc.com/web_materials/Manual/Vive/Vive_User_Guide.pdf)
  * [SteamVR Support pages](https://support.steampowered.com/kb_article.php?ref=5254-FJKZ-7829)

If you have a [Vive Pre development kit](https://developer.viveport.com/managed-assets/shared/desktop/vive/Vive_PRE_User_Guide.pdf), you may still be able to follow these same instructions to use WebVR, but there are no guarantees of stability nor performance. (It's worth noting that there are mostly only the modifications made between the Vive Pre and Vive consumer version are mostly slight changes to the aesthetics and comfort [e.g., the most obvious being the IPD adjustment knob and slight headstrap adjustments].)

The [Vive wireless motion controllers](https://www.vive.com/us/support/faqs/#Controllers) are [supported](https://iswebvrready.org/#gamepad-extensions) by the [Gamepad API (Extensions)](https://w3c.github.io/gamepad/extensions.html) in [these experimental Chromium WebVR builds](#instructions).

## Platform requirements

* **Graphics card:** [NVIDIA GeForce GTX 970](http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-970) / [AMD Radeon R9 290](https://www.amd.com/en-us/products/graphics/desktop/r9), or better.
* **CPU:** [Intel i5-4590](http://ark.intel.com/products/80815/Intel-Core-i5-4590-Processor-6M-Cache-up-to-3_70-GHz) / [AMD FX 8350](https://www.amd.com/en-us/products/processors/desktop/fx), or better.
* **Memory:** 4GB+ RAM.
* **Video output:** HDMI 1.4, [DisplayPort 1.2](http://www.displayport.org/faq/), or better.
* **USB ports:** one USB 2.0 (or faster) port.
* **OS:** [Windows 7 SP1](https://support.microsoft.com/en-us/help/15090/windows-7-install-service-pack-1-sp1) (64-bit) or newer.

You may download and run the [SteamVR Performance Test](http://store.steampowered.com/app/323910/) to ensure your machine meets the minimum requirements to enjoy VR in the HTC Vive.

You may wish to upgrade your Windows PC manually, order/build a new custom machine, or purchase a [prebuilt Vive-ready PC](https://www.vive.com/ready/).

## Software requirements

* You must be running [Windows 7 SP1](https://support.microsoft.com/en-us/help/15090/windows-7-install-service-pack-1-sp1) (64-bit) or newer. (Also, ensure you have installed the [Microsoft .NET Framework v4.6 or newer](https://www.microsoft.com/en-us/download/details.aspx?id=48137)).
* Download, install, launch, and configure the [Vive with SteamVR](http://www.vive.com/us/setup/). (The Vive makes use of [Valve](http://www.valvesoftware.com)'s [Steam](http://store.steampowered.com/) application for browsing, purchasing, downloading, and installing VR experiences. SteamVR is installed as a separate application and contains the required runtime to render experiences to the Oculus Rift.)

(If needed, refer to the [Vive User Guide](http://dl4.htc.com/web_materials/Manual/Vive/Vive_User_Guide.pdf) or the [SteamVR Support pages](https://support.steampowered.com/kb_article.php?ref=5254-FJKZ-7829).)

## Instructions

1. Download the [latest experimental Windows Chromium build (64-bit only)](https://webvr.info/get-chrome/) by [Brandon Jones](https://twitter.com/tojiro) (WebVR Platform Engineer, Google Chrome).
2. In the URL bar, enter `chrome://flags#enable-webvr` and select `Enabled` from the drop-down menu for the `Enable WebVR` flag setting.
3. In the URL bar, enter `chrome://flags#enable-gamepad-extensions` and select `Enabled` from the drop-down menu for the `Enable Gamepad Extensions` flag setting. (As an extension to the browser's [Gamepad API](https://w3c.github.io/gamepad/), [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html) are specifically required to enable support for motion-tracked VR controllers, vibration/rumble support and haptics, touchpad detection, etc.)
4. Launch the [SteamVR](https://support.steampowered.com/kb_article.php?ref=5254-FJKZ-7829) application.
5. Go enjoy some WebVR content!

<hr>

# Related links

* [[Chromium Release Notes|Release-Notes:-Chromium]]
* [[Chromium Developer Notes|Developer-Notes:-Chromium]]
* [Vive User Guide](http://dl4.htc.com/web_materials/Manual/Vive/Vive_User_Guide.pdf)
* [SteamVR Support pages](https://support.steampowered.com/kb_article.php?ref=5254-FJKZ-7829)
* [Vive video tutorials (official)](http://www.vive.com/us/support/)
* [UltraVR's Vive Guide (unofficial)](http://www.ultravr.org/htc-vive-guide/)
* [OpenVR SDK open-source project on GitHub](https://github.com/ValveSoftware/openvr)
* [OpenVR SDK documentation](https://github.com/ValveSoftware/openvr/wiki/API-Documentation)
* [SteamVR Community blog](https://steamcommunity.com/steamvr)
* [SteamVR Hardware](http://store.steampowered.com/hardware/)
