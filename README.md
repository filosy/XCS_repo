# XCSoar Custom Configurations and Data

This repository contains personal XCSoar resources and custom configuration files used for glider flight setup and map/waypoint management.

It includes:
- custom input event files (`.xci`)
- waypoint and task files (`.cup`)
- map files (`.xcm`)
- external resource links and download references

## Repository contents

### Custom input configuration

Active file:
- `xcsoar-input-v1.xci`

This file is a custom XCSoar input event definition used to override specific default bindings without modifying the original built-in `default.xci` file.

It includes:
- `S` → Speed-to-Fly / cruise force mode
- `V` → Vario / climb force mode
- `UP` / `DOWN` in the FLARM traffic modes → zoom in / zoom out

#### Speed-to-Fly / Vario actions

The file contains:

- `S` → sends `g,s1` via NMEA ports 1 and 2
- `V` → sends `g,s0` via NMEA ports 1 and 2

It also shows status messages and forces the XCSoar display mode:

- `UserDisplayModeForce forcecruise`
- `UserDisplayModeForce forceclimb`

This is useful when using compatible external devices such as XCRemote, XCNav, or XCVario.

#### FLARM traffic zoom

The file also customizes FLARM traffic zoom behavior:

- `UP` → `Traffic zoom in`
- `DOWN` → `Traffic zoom out`

This is applied within:
- `mode=default.Traffic`
- `mode=Display1.Traffic`
- `mode=Display2.Traffic`

These entries override the default traffic target navigation in those modes.

## How to use the `.xci` file

Copy the file into the XCSoar data directory, typically:

- Windows: `%LOCALAPPDATA%\XCSoarData\`
- Linux / Unix: `~/.xcsoar/`
- macOS: `~/XCSoarData/`
- Android / iOS: the app data directory used by XCSoar

Example path:

```text
XCSoarData/input/xcsoar-input-v1.xci
