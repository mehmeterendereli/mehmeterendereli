![Mehmet Eren Dereli — machinery, industrial automation and source-verifiable software](./assets/profile-hero.svg)

<p align="center">
  <a href="https://www.mehmeterendereli.com/en">Website</a> ·
  <a href="https://www.mehmeterendereli.com/en/open-source">Open-source portfolio</a> ·
  <a href="https://www.linkedin.com/in/mehmeterendereli">LinkedIn</a> ·
  <a href="mailto:info@mehmeterendereli.com">Email</a>
</p>

I build inspectable systems across mechanics, motion, heat, control and software. My public work connects practical Windows tools, large-format additive manufacturing and deterministic automation. My product interests also include privacy-first, on-device AI.

Public repositories show what can be read, run and tested today. Customer work, private source, internal architecture and unreleased commercial products remain private.

## Featured · OpenRelax PC Care

### Review maintenance. Understand CPU spikes.

[OpenRelax](https://github.com/mehmeterendereli/openrelax) combines a Windows maintenance interface with **Fotokapan**, a built-in recorder for sustained high-CPU episodes while the app is open, including in the tray. Start with a read-only check, inspect the selected operations, and confirm before interactive cleanup.

**2.4.0 source release · Windows PowerShell 5.1 · TR / EN · MIT · unsigned source**

**Start here:** [Install for the current user](https://github.com/mehmeterendereli/openrelax#install) · [Open the 2.4.0 release](https://github.com/mehmeterendereli/openrelax/releases/tag/v2.4.0) · [Download the verified release ZIP](https://github.com/mehmeterendereli/openrelax/releases/download/v2.4.0/OpenRelax-2.4.0.zip) · [Inspect SHA256SUMS](https://github.com/mehmeterendereli/openrelax/releases/download/v2.4.0/SHA256SUMS) · [Run from source](https://github.com/mehmeterendereli/openrelax#run-from-source)

**Maintenance you can inspect.** Corrupt settings stop scheduled cleanup. Recycle Bin, system-cache categories, developer caches, RAM trimming and DNS flushing are opt-in. Cleaning reports live file/byte progress; the read-only `-SelfTest` remains separate from maintenance.

**A record after the CPU spike.** Fotokapan runs inside OpenRelax without administrator rights or a scheduled task, records while the app is open, and separates measured interrupt/DPC load from unattributed CPU. It turns the last seven days into categorized findings, keeps a full records page, exports a Markdown report and can announce new spikes. Command-line recording is opt-in, masked and off by default; masking cannot guarantee removal of every secret. It is a high-CPU recorder, not a promise to diagnose every freeze.

**Evidence, not speed-up claims:** [eight verified TR/EN interface captures](https://github.com/mehmeterendereli/openrelax/tree/main/docs/screenshots) and [the 2.4.0 Windows checks](https://github.com/mehmeterendereli/openrelax/actions/runs/39076300291) cover the native UI, isolated safety, scan/cleanup, engine/unit contracts, renderer paths, installer contracts and the measured tray-footprint gate. A disposable hosted Windows runner also verifies the legacy Fotokapan SYSTEM-task lifecycle used for safe migration and removal. The release provides an unsigned source ZIP with SHA256SUMS—not a signed binary, stable binary distribution or LTS commitment—and real Windows Update restoration, reboot, RDP, Narrator and monitor-DPI scenarios remain release gates.

[Report a reproducible issue](https://github.com/mehmeterendereli/openrelax/issues/new) · [Contribute](https://github.com/mehmeterendereli/openrelax/blob/main/CONTRIBUTING.md) · [Security reporting](https://github.com/mehmeterendereli/openrelax/blob/main/SECURITY.md)

---

## Engineering · VORMETRA Slice

[An OrcaSlicer-based workspace](https://github.com/mehmeterendereli/vormetra-slice) for a design-stage pellet-fed large-format additive-manufacturing system, with a public G1000 profile and the Python `vera-control` bridge.

**Try it:** [Install and run the portable checks](https://github.com/mehmeterendereli/vormetra-slice#quick-start) · [Inspect the control bridge](https://github.com/mehmeterendereli/vormetra-slice/tree/main/vera-control) · [Run the self-contained validation demo](https://github.com/mehmeterendereli/vormetra-slice/blob/main/vera-control/README.md#portable-first-result)

`C++` · `Python` · `OrcaSlicer` · `HTTP / MCP` · `AGPL-3.0 + MIT`

[![Generated VORMETRA demo output: a 200 × 200 × 100 mm STL fits the configured 1000 × 1000 × 1000 mm software envelope. Bounding-box check only, not a print or hardware test.](https://raw.githubusercontent.com/mehmeterendereli/vormetra-slice/main/docs/portable-validation-proof.svg)](https://github.com/mehmeterendereli/vormetra-slice/blob/main/vera-control/README.md#portable-first-result)

<sub>Reproducible example output, not a live status or hardware certification. The demo generates this card from its JSON report; it does not run a slicer or a physical printer. Physical-machine completion, throughput, accuracy and production reliability are not established by this check.</sub>

## What I am building toward

- **Machines:** custom machinery, extrusion systems, CAD/CAM and production-oriented mechanical design.
- **Automation:** PLC/HMI, motor drives, thermal-zone control, retrofit and commissioning.
- **Software:** deterministic control interfaces, testable Python/C++ systems and source-verifiable workflows.
- **Private AI:** device-side, privacy-first product experiences; only publicly released evidence is described here.

## Evidence before claims

Every public project should make four things easy to inspect:

1. **Architecture** — components and trust boundaries are traceable from source.
2. **Reproduction** — clone, run and test commands match the current tree.
3. **Safety** — refusal and failure behavior sit beside the happy path.
4. **Maturity** — design targets, software checks and physical results are kept distinct.

## Work together

For an engineering project, a reproducible bug report or an open-source contribution, start with [email](mailto:info@mehmeterendereli.com) or [LinkedIn](https://www.linkedin.com/in/mehmeterendereli). Repository-specific fixes are best opened against the relevant project so the discussion stays connected to source and tests.

<sub>Based in İstanbul, Türkiye · Public engineering profile maintained with explicit evidence boundaries.</sub>
