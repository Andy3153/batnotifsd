<!-- vim: set fenc=utf-8 ts=2 sw=0 sts=0 sr et si tw=0 fdm=marker fmr={{{,}}}: -->
# Battery notifications daemon

## What
This is a Python script that sends notifications about the battery's status
(charger plugged in/unplugged, low/critical battery levels).

It's useful for window managers where you don't get this functionality out of
the box like in a desktop environment.

## Why
I wrote this because I simply could not find anything else that did the job 100%
right. The internet is full of shell scripts that just tap into
`/sys/class/power_supply` and take info from that in a `while true` loop with a
`sleep`, most don't even autodetect the laptop's battery and make you set a
variable for the right battery for you, or, even worse, manually edit the shell
script to put it in.

## How
This Python script uses the [pydbus](https://github.com/LEW21/pydbus) library to
get information directly from [UPower](https://upower.freedesktop.org/) through
[DBus](https://dbus.freedesktop.org/), and then send it back through DBus using
the `org.freedesktop.Notifications` bus, all in a
[GLib](https://pygobject.gnome.org/) loop.

## More info
- [pydbus documentation](https://pydbus.readthedocs.io/)
- [pydbus notification example](https://pydbus.readthedocs.io/en/latest/legacydocs/shortexamples.html?highlight=notifi#send-a-desktop-notification)
- [`org.freedesktop.UPower.device`](https://upower.freedesktop.org/docs/Device.html)
specification in the UPower Manual
