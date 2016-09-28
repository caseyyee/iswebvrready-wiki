# What is OSVR?

* [[Read about the OSVR project.|Instructions:-OSVR#what-is-osvr]]
  * [[Read the OSVR Platform instructions.|Instructions:-OSVR-(Platform)]]
  * [[Read the OSVR Headset ("Hacker Dev Kit") instructions.|Instructions:-OSVR-(Headset)]]

# Prerequisites

You can experience OSVR support in Firefox Nightly using one of the following VR headsets:

* [[<b>Oculus Rift</b>|Instructions:-Firefox-Nightly-for-Oculus-Rift-on-Windows]]
* [[<b>HTC Vive</b>|Instructions:-Firefox-Nightly-for-Oculus-Rift-on-Windows]]
* [[<b>OSVR Hacker Dev Kit</b>|Instructions:-Firefox-Nightly-for-Oculus-Rift-on-Windows]]

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

**Note:** The current implementation supports [Extended Mode](https://github.com/OSVR/OSVR-Docs/blob/master/Installing/RenderManager.md#what-is-render-manager-).

<hr>

# Related links

* [List of OSVR open-source projects (GitHub organization page)](https://github.com/OSVR/)
* [Index of OSVR documentation](https://github.com/OSVR/OSVR-Docs/)
* [Platform tracking issue for OSVR support in Firefox](https://bugzilla.mozilla.org/show_bug.cgi?id=1276712)
* ["OSVR Comes to WebVR" (Sensics blog post)](http://sensics.com/osvr-comes-webvr/)
* ["Why WebVR?" (Sensics blog post)](http://sensics.com/why-webvr/)
