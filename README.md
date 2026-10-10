# AETHER

AETHER is an **umbrella repository** — a collection of independent software projects kept in one place. It is not a single application: the projects share **no architecture, no code, and no build system**. Some are working software; others are reserved folders held for future work.

## Projects

| Directory | What it is | Stack | State |
|---|---|---|---|
| `UNMATCHED/` | **D1VI Tuner** — native Windows 11 performance toolkit: live CPU / memory / power monitoring, reversible power-plan, animation-effect, and per-game GPU-preference tweaks, working-set trimming, and a read-only startup inventory. Build instructions live in its own [README](UNMATCHED/README.md). | C++20, Qt 6 Widgets, CMake | Working app (`D1VITuner`, v1.0.0), built with MSVC x64 |
| `RisingStar/KONATA/` | **KONATA** — desktop authoring tool for fictional chat/story content, with a pixel-faithful chat renderer and PNG export. A nested independent git repo; its canonical home is [adamsalawu/KONATA](https://github.com/adamsalawu/KONATA). | C++17, Qt 6 Widgets, CMake | Early development (0.1.x); builds locally with MSVC |
| `RisingStar/MIYUKI/` | **MIYUKI Model Lab** — Python lab for developing a creative-writing language model: datasets, LoRA training, evaluation, and local inference. A nested independent git repo; its canonical home is [adamsalawu/MIYUKI](https://github.com/adamsalawu/MIYUKI). This is the model-development side — the future desktop writing application is not implemented there. | Python 3.10+, PyTorch, Transformers, PEFT/LoRA | Active; Phase 4C complete, 107 tests |
| `RisingStar/KAGAMI/`, `RisingStar/TSUKASA/`, `ROKI/`, `AllInOne/TOMURA/` | Reserved folders, currently empty | — | Placeholder |
| `Kenjaku/`, `Shinigami/` | Reserved folders; each holds only a small launcher script, no application source | — | Stub |

## Repository layout

```text
AETHER/
├── UNMATCHED/            # D1VI Tuner app (src/main.cpp, CMakeLists.txt, README.md)
├── RisingStar/
│   ├── KONATA/           # KONATA app (separate git repo, see below)
│   ├── MIYUKI/           # MIYUKI lab (separate git repo, see below)
│   ├── KAGAMI/           # empty, reserved
│   └── TSUKASA/          # empty, reserved
├── Kenjaku/              # stub (launcher script only)
├── Shinigami/            # stub (launcher script only)
├── ROKI/                 # empty, reserved
├── AllInOne/TOMURA/      # empty, reserved
└── devtools/             # local toolchain cache (gitignored, not source)
```

### Nested repositories

`RisingStar/KONATA` and `RisingStar/MIYUKI` are **independent git repositories** with their own remotes (`origin` pointing at `github.com/adamsalawu/KONATA` and `github.com/adamsalawu/MIYUKI`). The root `.gitignore` excludes them, so AETHER's own history does not track their files — do work in each directory against its own remote.

### devtools/

`devtools/` is a gitignored local toolchain cache, not project source: a Qt 6.8.1 `msvc2022_64` kit and a CMake 4.4.3 tree that the C++ projects build against. `RisingStar/KONATA/CMakeLists.txt` points at that Qt kit by default (overridable with `-DCMAKE_PREFIX_PATH=...`), so KONATA configures out of the box from this checkout.

## Getting started

Each project builds and runs on its own; there is no root-level build.

- **D1VI Tuner** — follow [UNMATCHED/README.md](UNMATCHED/README.md) (CMake + MSVC x64 + Qt 6).
- **KONATA** — follow [RisingStar/KONATA/README.md](RisingStar/KONATA/README.md) (CMake ≥ 3.21 + MSVC 2022 + Qt 6.8; first configure needs network for its JSON dependency).
- **MIYUKI** — follow [RisingStar/MIYUKI/README.md](RisingStar/MIYUKI/README.md) (Python 3.10+, `pip install -e ".[dev]"`; CPU-only friendly).

## Scope notes

- KONATA (chat/story presentation and authoring) and MIYUKI (creative-writing model development and story intelligence) both touch narrative content, but they share no code and neither depends on the other.
- UNMATCHED (Windows performance tooling) is unrelated to the other two.

## License

There is no `LICENSE` file at the root of AETHER. `RisingStar/MIYUKI` (a separate repository) carries its own MIT license; KONATA, UNMATCHED, and the placeholder folders currently include no license file.
