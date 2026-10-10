# D1VI Tuner

Native Windows 11 performance toolkit built with C++20, Qt 6 Widgets, and CMake.

## Build (MSVC x64)

From an x64 Visual Studio developer prompt, with Qt 6's `msvc2022_64` kit available:

```powershell
cmake -S . -B build -G "Visual Studio 17 2022" -A x64 -DCMAKE_PREFIX_PATH="C:/path/to/Qt/6.8.1/msvc2022_64"
cmake --build build --config Release
```

The app stores its own history and log under `%LOCALAPPDATA%\D1VI Tuner`. Changes are previewed before they are applied and journaled before mutation so they can be restored.

## Supported operations

* Live CPU, memory, battery/AC, power plan, process I/O rates, DXGI adapter names, and peak GPU-engine utilization when Windows exposes the PDH counter.
* Reversible selection of the built-in Balanced power plan. No plan is silently created or modified.
* Reversible current-user animation preference.
* Reversible per-game Windows GPU preference. The exact previous registry value is journaled before changing it, and the Gaming page can restore a D1VI-managed entry.
* Working-set trimming for accessible processes, without terminating them.
* Read-only startup inventory (Run keys and Startup folders). Startup entries are not removed or rewritten by this build.

GPU engine load is the busiest reported GPU engine, not a combined card percentage; it is marked unavailable if Windows does not expose the counter. GPU temperature, HAGS, and Game Mode state are not read. The Gaming page opens Windows Graphics/Power settings and the installed RTSS/Afterburner tools; it does not set an RTSS cap, change fan behavior, or apply global NVIDIA power settings.
