# ZombieMUD Core Lite for MUSHclient

ZombieMUD Core Lite is a small starter set of MUSHclient plugins for ZombieMUD.

It is meant for players who want the most useful quality-of-life plugins without loading the full ZombieMUD plugin collection.

Core Lite manages these plugins:

- `Message_Router.xml`
- `Combat_Manager.xml`
- `Know_Your_Audience.xml`
- `simplestepper.xml`

The manager plugin is:

- `ZombieMUD_Core_Lite.xml`

Core Lite does not replace the full `ZombieMUD_Core.xml`. It has a different plugin name, a different plugin ID, and its own command prefix: `zlite`.

## What It Does

Core Lite helps you:

- Check whether the lite plugin set is loaded.
- Load missing lite plugins.
- Reload the lite plugin set without closing your world.
- See the main commands for the included plugins.
- Toggle background sound playback in MUSHclient.

It does not change ZombieMUD itself. It only runs inside MUSHclient.

## Requirements

- MUSHclient 4.00 or newer.
- The ZombieMUD plugin files in your MUSHclient plugins folder.
- Lua scripting enabled in MUSHclient.

The expected plugin folder is usually:

```text
C:\Program Files (x86)\MUSHclient\worlds\plugins\Zombiemud Plugins
```

## Included Plugins

### ZombieMUD Core Lite

File:

```text
ZombieMUD_Core_Lite.xml
```

This is the small manager plugin. It checks, loads, and reloads only the lite plugin set.

Main commands:

```text
zlite
zlite status
zlite plugins check
zlite plugins load
zlite reload
zlite reload list
zlite sounds background
```

### Message Router

File:

```text
Message_Router.xml
```

This routes ZombieMUD channels and tells into miniwindows.

Useful commands:

```text
msgwin
msgreset
msgsize channels 800 20
msgsize tells 800 20
msgsize both 800 20
msglog
msglog on
msglog off
msgbell
msgbell on
msgbell off
msgchannels
```

Notes:

- `msgwin` shows or hides both message windows.
- `msgsize` changes miniwindow width and visible row count.
- The message windows can be dragged, resized, and scrolled.
- Message logging writes files under the MUSHclient `ZombieMush\Logs` folder.

### Combat Manager

File:

```text
Combat_Manager.xml
```

This tracks useful combat events, including vulnerability timing, combat rounds, scan output, and corpse handling.

Useful command:

```text
corpsemode <mode>
```

Examples:

```text
corpsemode off
corpsemode bury
corpsemode tin
```

Use `corpsemode off` if you do not want the plugin to send corpse-handling commands.

### Know Your Audience

File:

```text
Know_Your_Audience.xml
```

This watches the output from the `know your audience` spell and reports useful resistance information.

There is no normal command to run. Cast the spell in-game, and the plugin watches the spell output automatically.

It can report:

- Target health percentage.
- Damage types the target resists most.
- Damage types the target resists least.
- Resistance levels in an easier-to-read format.

### SimpleStepper

File:

```text
simplestepper.xml
```

This loads walking paths from a path file and lets you step through them one command at a time.

Useful commands:

```text
- <pathname>
.
..
```

Examples:

```text
- town
.
..
```

What those commands mean:

- `- town` loads a path named `town`.
- `.` sends the next command in the loaded path.
- `..` tries to step backward using the plugin's reverse-direction table.

By default, SimpleStepper looks for paths here:

```text
C:/Program Files (x86)/MUSHclient/worlds/paths/paths.path
```

Each path line should look like this:

```text
town=n;e;e;s;w
```

## Installation

1. Copy the plugin XML files into your ZombieMUD plugin folder.
2. Open your ZombieMUD world in MUSHclient.
3. Go to `File` -> `Plugins`.
4. Click `Add`.
5. Select `ZombieMUD_Core_Lite.xml`.
6. Click `OK`.

After loading Core Lite, type:

```text
zlite plugins load
```

That command tells Core Lite to try loading the four plugins it manages.

## First Commands To Try

After installation, try these in MUSHclient:

```text
zlite status
zlite plugins load
zlite reload
```

If the message windows are hidden, try:

```text
msgwin
```

If the message windows are too large or too small, try:

```text
msgsize both 800 20
```

## Reloading Plugins

You do not need to close your world just to reload these plugins.

Reload everything in the lite set:

```text
zlite reload
```

Reload one plugin:

```text
zlite reload messages
zlite reload combat
zlite reload audience
zlite reload stepper
```

Show reload targets:

```text
zlite reload list
```

## Status Checks

To see whether the lite plugins are loaded and enabled:

```text
zlite status
```

To check only plugin health:

```text
zlite plugins check
```

If something is missing, run:

```text
zlite plugins load
```

## Background Sounds

MUSHclient can either play sounds only while it is focused, or keep playing sounds while it is in the background.

Toggle that setting with:

```text
zlite sounds background
```

## Troubleshooting

### Core Lite loaded, but other plugins are missing

Run:

```text
zlite plugins load
```

If a plugin is still missing, make sure the XML file is in the same plugin folder as `ZombieMUD_Core_Lite.xml`.

### Message windows do not show

Try:

```text
msgwin
```

Then check:

```text
zlite status
```

### Message windows are the wrong size

Try:

```text
msgsize both 800 20
```

You can change the numbers. The first number is width in pixels. The second number is visible rows.

### SimpleStepper cannot find paths

Make sure this file exists:

```text
C:/Program Files (x86)/MUSHclient/worlds/paths/paths.path
```

Then make sure it contains path lines like:

```text
town=n;e;e;s;w
```

### I edited a plugin and want MUSHclient to use the new version

Run:

```text
zlite reload
```

Or reload only the plugin you changed:

```text
zlite reload messages
zlite reload combat
zlite reload audience
zlite reload stepper
```

## Full Core vs Lite Core

Use `ZombieMUD_Core_Lite.xml` if you only want:

- Message windows.
- Combat management.
- Know Your Audience parsing.
- SimpleStepper path walking.

Use the full `ZombieMUD_Core.xml` if you want the larger ZombieMUD plugin set.

The Lite Core uses `zlite` commands so it does not conflict with the full Core's `zombie` and `zreload` commands.

## Files In The Lite Set

```text
ZombieMUD_Core_Lite.xml
Message_Router.xml
Combat_Manager.xml
Know_Your_Audience.xml
simplestepper.xml
```

## License

No license has been selected yet. Add a license before publishing publicly if you want others to reuse or modify the plugins.
