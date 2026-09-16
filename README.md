# FlightSimShaker

A bass shaker (tactile transducer) driver for flight simulators. It turns simulator telemetry into
low-frequency audio for ButtKicker / Dayton style shakers.

Currently supported: **IL-2 Sturmovik: Great Battles** and **IL-2 Sturmovik: Korea**.

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
