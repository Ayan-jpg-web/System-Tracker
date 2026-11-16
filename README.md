# System Monitor

A native Android app (Kotlin + Jetpack Compose) that displays:

- **CPU** — per-core usage % and current frequency (read from `/proc/stat` and `/sys/devices/system/cpu/cpuN/cpufreq/scaling_cur_freq`)
- **Memory** — used / available RAM, low-memory state
- **Battery** — charge %, health, charging status, temperature, voltage, technology, live current draw
- **GPU** — vendor / renderer / GL version strings (queried via a throwaway EGL context)

Refreshes automatically every ~1.2 seconds.

### A note on GPU monitoring
Android does not expose a public API for live GPU utilization (no "GPU %" like CPU has). This app shows GPU **identity** info (vendor, renderer, driver version) via OpenGL ES. True real-time load numbers exist only in vendor-specific files under `/sys/class/kgsl/` or similar, which require root to read reliably across devices — so they're intentionally left out rather than faked.

### Permissions
No dangerous permissions are requested. Everything reads from public system files/APIs available to any app.
