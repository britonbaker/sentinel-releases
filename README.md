# Sentinel for Mac

A native menu bar app that watches for hardware activity while you are away from your Mac. It can request the macOS lock screen and save a local incident when a selected trigger fires.

**[Download Sentinel for Apple silicon](https://github.com/britonbaker/sentinel-releases/releases/latest/download/Sentinel-0.3.1-21-arm64.zip)**

Requires an M1 or newer Mac and macOS 14 or later. Local Mac protection needs no account or subscription.

## Install

1. Unzip the downloaded archive.
2. Drag **ScreenSentinel** onto **Applications**.
3. Open it from Applications. Its setup window walks through **Input Monitoring** and **Accessibility**.
4. Click the shield in the menu bar and choose **Test detection**. Check the hinge angle and physical-input counter before arming.

If macOS asks you to quit and reopen after granting access, do that and reopen setup. Camera, microphone and the closed-lid helper are optional; they are not required to start guarding.

## Use

Choose **Arm**. The button counts down for 10 seconds so you can leave the Mac in position. The default duration is **Until stopped**.

Selected physical input, USB attachment, wake, or hinge movement of 2 degrees or more can trigger it. Sentinel saves an incident, disarms, then requests the lock screen. Sign in, acknowledge the incident, and arm again when ready. It does not rearm itself.

For a first lock test, save your work, keep the lid open, arm, wait for the countdown to finish, then move the lid by at least 3 degrees. Sign back in and check the incident. The hinge sensor is hardware-dependent; if unavailable, disable that trigger in Settings and test the supported input/USB triggers instead.

Optional camera clips start **after** a trigger and stay on your Mac. There is no continuous recording or pre-event buffer. Audio is separately enabled. Capture through lock/sleep is best effort, and a closed lid can block the camera or disable the microphone.

## Mac-to-Mac remote desktop

Choose **Open another Mac** in Sentinel Settings, then **Pair a Mac**. Copy the code from **Set up remote desktop** on the other Mac and paste it into the single code field. Pairings stay in this Mac's Keychain. No iCloud account is required for paired desktop access.

Choose **Open desktop** to use its regular desktop in a resizable or full-screen window with mouse, keyboard and scrolling. The remote Mac must be unlocked and have paired desktop access approved. **Mac sign-in** in the viewer's options retains the existing macOS Screen Sharing sign-in path. Locking this Mac closes its outgoing viewers; remote input does not disable physical protection on the target Mac. Away access uses Tailscale on both Macs.

The Mac viewer passed generated-desktop loopback checks; a connection between the owner's two physical Macs and an away-network test remain unverified.

## iPhone and remote desktop

The optional iPhone companion is in private TestFlight testing. Enable paired remote desktop in the Mac's Sentinel setup and allow Screen Recording when requested, then paste its pairing code into the phone app. A paired phone can control the existing desktop while the Mac is unlocked. Locking, sleep or a user switch ends access.

Trackpad mode starts automatically. One finger moves the cursor, a tap clicks, two fingers slide to scroll or tap to right-click, and a deliberate pinch zooms the view. Other controls are in the ellipsis menu. A subtle menu-bar dot and panel status show an active connection. Away access currently requires a reachable private network such as Tailscale on both devices.

To arm or disarm from the iPhone in the current beta, enable iPhone sync and **Allow controls from iPhone** in the Mac's Sentinel settings, using the same Apple Account. Remote desktop pairing alone currently enables screen access rather than guard controls.

## Updates and verification

**Check for Updates** is in Settings. Updates wait for guarding, recording, and closed-lid work to finish before restarting.

The app is Developer ID signed and Apple notarized. The ZIP used by the updater also has an Ed25519 signature. [Release assets and checksums](https://github.com/britonbaker/sentinel-releases/releases/latest) are public; source code, preferences and recordings are not included.

This is an early preview. Signing, notarization, and local regression checks do not establish hardware behavior on every Mac. Test detection and one lock on your own Mac before relying on it.
