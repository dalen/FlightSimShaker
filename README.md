# FlightSimShaker

A bass shaker (tactile transducer) driver for flight simulators. It turns simulator telemetry into
low-frequency audio for ButtKicker / Dayton style shakers.

Currently supported: **IL-2 Sturmovik: Great Battles**, **IL-2 Sturmovik: Korea**,
**War Thunder** (aircraft) and **DCS World**.

## Download

Get `FlightSimShaker-win-Setup.exe` from the
[latest release](https://github.com/dalen/FlightSimShaker/releases/latest) and run it. The app
installs for the current user and updates itself.

Without a license, FlightSimShaker plays for 20 minutes each time it starts.
[Buy a license](https://buy.polar.sh/polar_cl_eDKNGm1BVYKm2ovCDO2iccWN5m9Wz7j1SXziX4RLTIS) (one-time
purchase, includes updates) and enter the key from the email on the app's *License* tab. Your keys
and activations are in the [customer portal](https://polar.sh/flightsimshaker/portal).

The installer isn't code-signed yet, so Windows may show "Windows protected your PC". Click
**More info**, then **Run anyway**.

## IL-2 setup

Add this to `data/startup.cfg` in the IL-2 installation directory. The app's *Simulators* tab
shows the same snippet and can copy it for you.

```
[KEY = telemetrydevice]
    addr = "127.0.0.1:29373"
    decimation = 1
    enable = true
[END]
[KEY = motiondevice]
    addr = "127.0.0.1:29373"
    decimation = 1
    enable = true
[END]
```

If another program already receives IL-2 telemetry, keep its `addr` and add ours as
`addr1 = "127.0.0.1:29373"` in both sections.

## War Thunder setup

There's nothing to set up. While you're in a battle, War Thunder shares its instruments on this
PC, and the app reads them while you're flying. War Thunder reports less than the other
simulators: it doesn't report gun fire, hits, ground contact or height above ground, so the
weapon, impact, touchdown, rolling and belly landing effects stay silent. Stall buffet is worked
out from the angle of attack. Ground vehicles aren't supported.

## DCS World setup

DCS only shares telemetry with export scripts, so the app installs one for you. Click
**Install** in the DCS section of the app's *Simulators* tab, then start a mission. Other export
scripts you use, such as SRS, Tacview or DCS-BIOS, keep working. **Remove** takes the script out
again.

DCS has no hit events, so hits are felt when a part of the aircraft fails, and not every aircraft
reports failures. It doesn't report afterburner use, so the WEP & afterburner effect stays silent.
