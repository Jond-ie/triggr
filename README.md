<p align="center"><img src="https://jond-ie.github.io/repo/assets/triggr.png" width="96" alt=""></p>

<h1 align="center">Triggr</h1>

<p align="center">
  <b>Make any button, gesture or event do anything you want.</b><br>
  Like Activator, rebuilt for iOS 15–18 · Rootless (Dopamine) · Touch ID and Face ID
</p>

<p align="center">
  <a href="https://jond-ie.github.io/repo/triggr/"><img src="https://img.shields.io/badge/Website-Triggr-blue" alt="Website"></a>
  <a href="https://jond-ie.github.io/repo/"><img src="https://img.shields.io/badge/Install-Jond--ie's%20repo-blue" alt="Install from Jond-ie's repo"></a>
  <a href="https://github.com/Jond-ie/triggr-beta/releases"><img src="https://img.shields.io/badge/latest-2.0.0%20beta%207.1-orange" alt="2.0 Beta 7.1"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/1.x%20source-GPLv3-lightgrey.svg" alt="GPL-3.0"></a>
</p>

<p align="center">
  <img src="screenshots/9-triggers.png" width="200" alt="The list of triggers">
  <img src="screenshots/5-picker.png" width="200" alt="The action picker">
  <img src="screenshots/12-ifelse.png" width="200" alt="If / Otherwise steps">
</p>

> **This repo** holds the open 1.x source (GPLv3) and is the place for [bug reports and requests](../../issues).
> Triggr 2.0 and later are closed source; get them from [the repo](https://jond-ie.github.io/repo/) or
> [triggr-beta](https://github.com/Jond-ie/triggr-beta/releases) (RootHide builds there too, untested).
> Tweak developers: [libtriggr](https://github.com/Jond-ie/libtriggr) (MIT).

## How it works

1. **Pick a trigger:** a button press, a swipe, a gesture, or something that happens, like your AirPods connecting.
2. **Pick what it does:** open an app, flip a switch, run a Shortcut, or a whole list of steps. **Test** runs it right away.
3. **Pick where:** everywhere, the Home Screen, in apps, the Lock Screen, or just inside one app.

All in **Settings → Triggr** or the **Triggr app**. Nothing changes until you assign something.

## Ideas to start with

| When… | …do this |
|---|---|
| Double-tap the status bar | Flashlight on / off |
| Hold volume down | Play / pause music |
| Shake | Jump back to the last app |
| Slide in from the left edge | App Switcher |
| Three-finger tap in any app | Screenshot |
| Flick up on the Camera icon | Start screen recording |
| Your AirPods connect | Open your music app and play |
| You join your home Wi-Fi | Low Power Mode off |
| Weekdays at 23:00 | Do Not Disturb and Dark Mode on |
| Plug in the charger | Say the battery level out loud |
| Lock + volume up | A menu of your favourite actions |
| Cover the top of the phone | Mute, only if music is playing |

## Everything it can do

Buttons, swipes, multi-finger gestures, sensors and events (a Wi-Fi network, a charger, your AirPods) can run
almost anything on the phone, as a single action or a list of steps with If / Otherwise and Only If conditions.
**[See the full list on the website](https://jond-ie.github.io/repo/triggr/)**, with what's new in 2.0 marked.

## Install

1. Add **https://jond-ie.github.io/repo/** to Sileo or Zebra (or open it on your iPhone and tap **Add to Sileo** / **Add to Zebra**).
2. Install **Triggr**. AltList and PreferenceLoader come with it.
3. Respring, then open **Triggr** from the Home Screen or **Settings → Triggr**.

## Light by design

- **Zero cost until you use it.** Every sensor, timer and gesture only exists while something is assigned to it. Nothing polls. Apps only get a tiny relay that stays silent unless a status bar or shake trigger is assigned.
- **Your buttons stay yours.** Unassigned buttons work exactly like before, waking the phone always works, and Emergency SOS is never touched.
- **Private.** Nothing listens on the network. Notification triggers only see which app posted, never what it says. The optional API is off by default and can only run your own setup.

## Tested on

Every arm64 and arm64e iPhone on iOS 15–18 with Dopamine. Checked by hand on:

| Chip | Buttons | iOS |
|---|---|---|
| A10 | Home / Touch ID | 15.8.6 |
| A11 | Home / Touch ID | 16.7 |
| A13 | Face ID | 16.2 |
| A13 | Home / Touch ID | 17.5.1 |
| A13 | Face ID | 18.6.2 |

On Face ID iPhones the Home button and Touch ID groups are hidden and the lock button is the **Side Button**.
If anything ever puts you in safe mode, uninstall Triggr from your package manager and [report it](../../issues/new/choose).

## More screenshots

<p>
  <img src="screenshots/1-main.png" alt="Main page with trigger search" width="200">
  <img src="screenshots/14-onlyif.png" alt="Only If conditions" width="200">
  <img src="screenshots/11-edges.png" alt="Screen edges" width="200">
  <img src="screenshots/10-combos.png" alt="Lock + Volume combos" width="200">
  <img src="screenshots/4-statusbar.png" alt="Status Bar triggers" width="200">
  <img src="screenshots/15-actionbutton.png" alt="Action button" width="200">
  <img src="screenshots/7-app.png" alt="One app's own triggers" width="200">
  <img src="screenshots/16-libtriggr.png" alt="Actions from other tweaks via libtriggr" width="200">
</p>

<details>
<summary><strong>Full documentation</strong> (every page, trigger and action)</summary>


The details for every page, trigger and action. Written for 1.5; 2.0 adds to it (see the lists above).

### Getting around

- **Main page:** Enabled, the places, In Specific Apps, All Assignments, Menus,
  Options and Profiles & Sharing. The search field finds any trigger.
- **A place:** an **Assigned** row (tap to change, swipe to remove, or Remove
  All), then one row per kind of trigger. A place's assignment replaces
  Anywhere's for the same trigger.
- **In Specific Apps:** inside the chosen app its assignments replace In Apps' and
  Anywhere's; everywhere else nothing changes.
- **The action picker:** what's picked on top, then Recently Used and the
  categories, a search field, and **Test** to run it right away.
- The **Triggr app** shows the same pages as Settings.

### Triggers

| Group | Triggers | Behaviour |
|---|---|---|
| Home Button | Single, Double, Triple, Short Hold, Long Hold | Replaces the system press when assigned (see **Replace Button Actions**). If Triple is assigned, a double press waits 0.35 s. |
| Touch ID | Light Double Tap; Finger Rest, Finger Match (Lock Screen) | Light Double Tap replaces Reachability; Finger Rest and Match run alongside unlocking. |
| Lock / Side Button | Single, Double, Triple, Hold | See **Lock button** below. On Face ID devices an assigned Double or Triple Press replaces Wallet / Apple Pay or the Accessibility Shortcut. |
| Volume Buttons | Up, Down, Up Hold, Down Hold, Up then Down, Down then Up, Press Both, Hold Both | A press replaces the volume step; a hold fires after 0.5 s. |
| Lock + Volume (Side + Volume on Face ID) | Up Press, Down Press, Up Hold, Down Hold | Both buttons together. A press replaces the lock and the volume step (and the screenshot on Face ID); with a Hold assigned too, the press runs on release. Holds fire after 0.5 s and run alongside iOS, so the power-off slider and Emergency SOS still appear. |
| Mute Switch | Silent, Ring, Toggled | Replaces muting / unmuting when assigned. |
| Status Bar | Tap, Double Tap, Hold; Left / Right Tap, Double Tap, Hold; Swipe Left, Swipe Right | Home Screen, Lock Screen and in apps. Left and Right are each half of the bar and run instead of the plain trigger on that side. Single taps can be turned off (**Options → Status Bar Single Tap**); they're off by default on Face ID iPhones, where a tap at the top can start pulling down Control Center. Swiping down stays iOS's. |
| Screen Edges | Slide In from Left / Right; Two-Finger Slide In from Left / Right | SpringBoard system gestures: over apps, on the Home Screen and the Lock Screen. One-finger Slide In from Left takes the place of an app's swipe back; the two-finger versions (as in Activator) don't. |
| Home Screen Icons | Flick Up, Down, Left, Right | A quick flick that starts on an app or folder icon. |
| Home Screen Gestures | Pinch In, Spread, Two-Finger Swipe Up / Down, Double Tap Empty Space | On the Home Screen pages; one-finger scrolling, Spotlight and icons work as before. Ignored while editing or with a folder open. |
| Motion | Shake Device | iOS's own shake detection: no sensor runs for Triggr. |
| Proximity Sensor | Cover, Wave | The sensor stays on only while one is assigned and the screen is on. |
| Charger & Headphones | Charger, Headphones connected / disconnected | Observed only while assigned. |
| Phone Calls | Incoming Call, Call Answered, Outgoing Call, Call Ended | CallKit's public observer: the Phone app, FaceTime and other calling apps. With Live Voicemail on, a call that goes to voicemail counts as answered. |
| Notifications | Any Notification | Only which app posted, never what it says. For one app, use Custom Events. |
| Music | Playback Started, Paused or Stopped, Song Changed | Any app in Now Playing. Changes caused by Triggr's media actions are ignored for a second. |
| State Changes | Wi-Fi, Bluetooth, Low Power on / off; joined / left a network; Device Locked / Unlocked; Screen On / Off | Changes Triggr causes itself are ignored for a second, so assignments can't loop. |
| Custom Events | A specific Wi-Fi network, a specific Bluetooth device (connected / disconnected), battery above / below X %, an app opened, **a notification from an app**, a scheduled time (every day, weekdays, weekends or chosen days), a flick on one app's icon | Networks and devices are picked from your saved ones. Notifications only count which app posted, never what it says. |

### Actions

- **System:** Go to Home Screen, App Switcher, Last App, Quit Current App, Control
  Center, Notification Center, Spotlight, Reachability, Siri, Take Screenshot,
  Screen Recording (start / stop, like Control Center's button), Close Background Apps
  (clears the App Switcher except the app you're in and the one playing audio),
  Vibrate, and Do Nothing (takes a trigger away from iOS without running anything).
- **Power:** Sleep (a lock button press: the screen turns off and the phone
  locks, as the button does), Lock Device (locks but leaves the screen on), Respring,
  Power Off Slider, Safe Mode, Restart, Power Off. Safe Mode restarts SpringBoard through ElleKit's own Safe Mode (no tweaks,
  Triggr included) until it's left from the Safe Mode screen. Restart and Power
  Off act at once, without asking, and the jailbreak stays off until Dopamine is
  run again; the picker warns before adding any of these.
- **Switches** (Toggle / Turn On / Turn Off): Flashlight, Wi-Fi, Bluetooth, Airplane
  Mode, Cellular Data, Do Not Disturb, Low Power Mode, Rotation Lock, Mute, Dark
  Mode, Night Shift, Auto-Brightness, Keep Screen Awake (until the next respring),
  Location Services.
- **Media:** Play/Pause, Next, Previous, Volume Up, Volume Down, AirPlay Picker (the system
  AirPlay menu), Play on iPhone, and AirPlay To… (a speaker or TV picked from the ones on
  your network, or typed; Settings asks SpringBoard to find them).
- **Levels:** Brightness %, Media Volume %, Ringer Volume %.
- **Open:** an app, a Settings page, a Shortcut, a URL.
- **Text & Commands:** Show Message, Speak Text, Run Command
  (`/var/jb/bin/sh -c` as **mobile**, with an explicit PATH; see **triggrd** below).
- **Menus:** a pop-up list of actions to choose from (Triggr → Menus).
- **Extensions:** other packages can add their own category of actions (see
  [EXTENSIONS.md](EXTENSIONS.md)); for example EQELinker adds "EQE Presets".
- **Recently Used** keeps your last six picked actions one tap away, and the
  **Test** button (top right) runs what's picked right away.

Tick several actions to run them in order. **Order & Pauses** reorders them and
adds pauses between them. Tap an action there to add a pause after it. Pauses
left dangling after an action is removed are cleared automatically. Adding an
action that conflicts with the list shows a warning: something after Respring,
Toggle and On/Off for the same switch, or two full-screen panels without a pause.
If a switch is the only action picked, picking another of its options (say Toggle
after Flashlight On) replaces it instead.

### Replace Button Actions

**Options → Replace Button Actions** (on by default) decides what an assigned
button press does to the button's own action:

- **On:** it runs instead, like Activator: an assigned Home press doesn't go Home,
  an assigned volume press doesn't change the volume, an assigned lock press
  doesn't lock, an assigned mute switch flip doesn't mute. To keep the button's
  own action as well, add the matching action to the list (Go to Home Screen,
  App Switcher, Siri, Reachability, Volume Up / Down, Sleep, Power Off Slider,
  Mute On / Off).
- **Off:** every press reaches iOS untouched and Triggr's actions run alongside.

Touch ID Finger Rest / Match, volume holds and Up then Down always run alongside.

### Lock button

With Replace Button Actions on, the lock / side button works like Activator's:

- An assigned **Single Press** runs instead of locking. When Double or Triple
  Press is assigned too, presses wait 0.4 s after the last one to be counted.
- An assigned **Hold** runs instead of the power-off slider (or Siri).
- A count with nothing assigned is handed back to iOS: it still locks, opens
  Wallet or runs the Accessibility Shortcut.
- A press that starts on a dark screen always just wakes the phone.
- Four or more presses are never acted on, so Emergency SOS keeps working.

### Lock Screen

Apps, URLs, Shortcuts and Settings pages can't open over the Lock Screen, so they
wait until you unlock. iOS's own unlock action block
(`SBLockScreenManager setUnlockActionBlock:`) runs them once you authenticate. With
**Commands Need Passcode** on (the default), shell commands wait too when a
passcode is set.

### triggrd

On iOS 18 SpringBoard isn't allowed to start programs, so Run Command and
extension actions are handed to **triggrd**, a small daemon (running as mobile)
installed with Triggr. It only runs commands and extension actions that are in
your own assignments or menus. On iOS 15–17 SpringBoard starts them itself.

### Extras

- **Profiles & Sharing:**
  - Save your setup as a profile and switch between profiles.
  - **Export** a setup as a `.json` file (share sheet), or **Import** one from
    Files. Import keeps only known settings and value types, shows a summary
    (assignments, menus, shell commands, URLs) and warns about shell commands
    before replacing anything. Export warns when the setup includes Wi-Fi or
    Bluetooth names or shell commands.
  - **Reset to Defaults** clears everything except saved profiles.
- **Options → Block List:** triggers are ignored inside chosen apps.
- **Options → Show Action Banners:** a small pill naming what just ran.

### API (for other tweaks and scripts)

Off by default: **Settings → Triggr → Options → Allow API**. Darwin notifications carry no
sender, so any process could post one. That's why the API can only run
**built-in actions, your assigned triggers and your menus**, never arbitrary shell
commands, URLs or apps. Profiles and imports never switch it on.

- Tweaks: `notify_post("com.johndie.triggr/api/run/<action>")`, `…/api/trigger/<trigger>`,
  `…/api/menu/<menu id>`.
- Command line: `triggr list`, `triggr run toggle.flashlight`,
  `triggr trigger statusbar.doubletap`, `triggr menu Quick`.
- Shortcuts: use the **Run Script Over SSH** action (host `127.0.0.1`, user
  `mobile`) with a `triggr` command. This needs OpenSSH.

There's no `triggr://` URL scheme. iOS only opens schemes that belong to an
installed app, and the request fails in the calling app before SpringBoard sees
it.

### Notes and limits

- **Menus** don't open while the device is locked.
- **Scheduled** events are skipped if iOS runs the timer more than 5 minutes late.
- Taking an AirPod out can count as "Headphones Disconnected".
- Control Center's Wi-Fi button only disconnects from the network; Wi-Fi stays on.
- **Last App** only knows the apps opened since the last respring.
- Turning **Dark Mode** on or off ends an automatic appearance schedule.
- Not offered: headset button, VPN and Personal Hotspot.

## Bugs and feature requests

Use [**Issues**](../../issues/new/choose) and include your **device chip, iOS
version, jailbreak and Triggr version**. Beta builds and their feedback live in
[triggr-beta](https://github.com/Jond-ie/triggr-beta).

### Getting a crash log

1. Open **Settings → Privacy & Security → Analytics & Improvements → Analytics Data**.
2. Find the entry from the time of the crash. Look for **SpringBoard**,
   **Preferences** or **Triggr** in the name.
3. Tap it, then share or copy the text into your crash report.

**Check before posting:** crash logs and exported setups can include personal
details. Examples are app names, Wi-Fi network or Bluetooth device names used in
your events, and shell commands. Remove anything you don't want public.

## Building

Install from [Jond-ie's repo](https://jond-ie.github.io/repo/) unless you want to
change the code. You need [Theos](https://theos.dev/docs/installation) with an iOS
SDK (built against 16.5 from [theos/sdks](https://github.com/theos/sdks)) and the
rootless scheme; AltList is vendored in `vendor/` for linking.

```bash
make package FINALPACKAGE=1 THEOS_PACKAGE_SCHEME=rootless
```

The Makefile builds arm64. Release builds add arm64e (`ARCHS="arm64 arm64e"`),
which needs a clang with the current arm64e ABI (Xcode's, or upstream LLVM 20 or
newer).

> AI assisted in development (Claude Code), all testing and debugging done by me on device.

## License and credits

The 1.x source in this repo is free software under the [GNU General Public License v3.0](LICENSE). Triggr 2.0
and later are closed source; [libtriggr](https://github.com/Jond-ie/libtriggr) is MIT.

- **Triggr** by **Jond-ie** ([Jond-ie's repo](https://jond-ie.github.io/repo/)).
- Inspired by **Activator** by Ryan Petrich.
- **Snapper 3** and **CopyLog** actions contributed by [@qnblackcat](https://github.com/qnblackcat) in #4.
- **[AltList](https://github.com/opa334/AltList)** by opa334 (Lars Fröder), MIT
  License; its files in `vendor/` keep their own license ([vendor/AltList-LICENSE](vendor/AltList-LICENSE)).
- Built with [Theos](https://theos.dev/).

</details>
