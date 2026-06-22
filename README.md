# Alert Script

`alert.ini` is a simple adiIRC script for per-window message alerts with sound, temporary alert timers, ignore lists, and persistent defaults.

## What It Does

- Toggles alerts for the current channel or query
- Supports `on`, `off`, `all`, and temporary durations like `10s`, `5m`, and `2h`
- Plays a sound when a watched window receives a message
- Lets you ignore specific nicks
- Saves persistent default commands to a local text file

## Install

1. Open adiIRC.
2. Load `alert.ini` as a script.
3. Restart or reload scripts if needed.

## Configuration

Edit the sound path near the top of `alert.ini`:

```text
run -h powershell -Command "(New-Object Media.SoundPlayer 'C:\Windows\Media\Windows Notify.wav').PlaySync()"
```

Replace the `.wav` path with the sound file you want to use.

## Commands

- `/alert` - toggle alert for the current channel/query
- `/alert on [channel/nick/all] [time]` - enable an alert, optionally with a temporary duration
- `/alert off [channel/nick/all] [time]` - disable an alert, optionally with a temporary duration
- `/alert cooldown [time]` - set the sound cooldown, for example `10s`, `5m`, or `2h`
- `/alert ignore nick` - ignore alerts from a nick
- `/alert ignore list` - list ignored nicks
- `/alert unignore nick` - stop ignoring a nick
- `/alert unignore all` - clear the ignore list
- `/alert list` - list enabled alerts
- `/alert defaults` - list persistent default commands
- `/alert setdefault [command]` - save a command as a persistent default
- `/alert resetdefault` - remove all persistent default commands
- `/alert restoredefaults` - reset session state and reapply saved defaults
- `/alert help` - show help

## Default Storage

Persistent defaults are stored in:

```text
alert_defaults.txt
```

The file is written in the script directory.

## Notes

- Alerts are reset on adiIRC restart and restored from saved defaults.
- Temporary alerts use timers and automatically expire.
- The script only alerts for windows that are currently enabled.
