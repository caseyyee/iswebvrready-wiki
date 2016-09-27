# What is OSVR?

[Open-Source Virtual Reality (OSVR)](http://www.osvr.org/) is an open-source project (released under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0)) with two main goals:

1. Provide an open-source software platform (SDK) as an abstraction layer for various VR headsets and operating-system configurations.
2. Release open-source VR hardware as an alternative to proprietary ones. Current OSVR headsets are being sold as [Hacker Dev Kits](http://www.osvr.org/buy/) (designed by [Razer](http://www.razerzone.com/) and [Sensics](http://sensics.com/), and manufactured by [Razer](http://www.razerzone.com/)).

The intent is build out and prove an open software platform that can support various VR headsets (e.g., Oculus Rift, HTC Vive, PSVR, etc.) and peripherals (including but not limited to VR controllers).

It's worth nothing that [OSVR](http://www.osvr.org/) and [Valve](http://www.valvesoftware.com/)'s [OpenVR](https://github.com/ValveSoftware/openvr) (the SDK used by the HTC Vive's [SteamVR](http://store.steampowered.com/steamvr) engine) are two separate projects, though they have similar goals.

# Prerequisites

You can experience OSVR support in Firefox Nightly using one of the following VR headsets:

* [[Oculus Rift|Instructions:-Firefox-Nightly-for-Oculus-Rift-on-Windows]]
* [[HTC Vive|Instructions:-Firefox-Nightly-for-Oculus-Rift-on-Windows]]
* [[OSVR Hacker Dev Kit headset|http://www.osvr.org/buy/]]

# Instructions

1. Download and install the latest [Firefox Nightly](https://nightly.mozilla.org/) build for Windows (see the complete [[instructions for Firefox Nightly on Windows here|Instructions:-Firefox-Nightly-for-Oculus-Rift-on-Windows]]).
2. Once Firefox Nightly is launched, enter `about:config` in the URL bar, which will bring up a list of configurable Firefox settings.
3. Search for `dom.vr.osvr.enabled`, and set that field to `true`.
4. While still in `about:config`, search for these following settings and fill in the appropriate paths for the OSVR libraries (DLLs available both in the Runtime and SDK installers):
  1. `gfx.vr.osvr.clientKitLibPath`
  2. `gfx.vr.osvr.clientLibPath`
  3. `gfx.vr.osvr.commonLibPath`
  4. `gfx.vr.osvr.utilLibPath`
5. Plug in the VR headset of your choice.
6. Start the OSVR server.
7. Restart Firefox Nightly.
8. Enjoy some WebVR content!

**Note:** The current implementation supports Extended Mode.

<hr>

# Related links

* [List of OSVR open-source projects (GitHub organization page)](https://github.com/OSVR/)
* [Index of OSVR documentation](https://github.com/OSVR/OSVR-Docs/)
* [Platform tracking issue for OSVR support in Firefox](https://bugzilla.mozilla.org/show_bug.cgi?id=1276712)
* ["OSVR Comes to WebVR" (Sensics blog post)](http://sensics.com/osvr-comes-webvr/)
* ["Why WebVR?" (Sensics blog post)](http://sensics.com/why-webvr/)
