# drive-bays

Hot-swappable bays for 3.5" and 2.5" hard drives, with per-bay power switching and temperature monitoring.

## Goals

- Mechanical bays accepting 3.5" and 2.5" drives (3D-printable or off-the-shelf frame).
- Per-bay power control (staggered spin-up, safe power-off).
- Per-bay temperature sensing with fan control and over-temperature cut-off.

## Toolchain

- **KiCad**: schematics and PCB.
- **PCB trace calculator**: trace width and current sizing for the power paths.
- **PSpice**: simulation of the power-switching and sensing circuits.
- **FreeCAD** or **Fusion 360**: mechanical design of the bays. Fusion 360 depends on the student licence, which is not installed yet; FreeCAD is the default until then.

## Status

Concept phase. See [PROJECT_LOG.md](PROJECT_LOG.md).
