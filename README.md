# drive-bays

Hot-swappable bays for 3.5" and 2.5" hard drives, with per-bay power switching and temperature monitoring.

## Goals

- 10 hot-swappable bays: 5 for 3.5" drives and 5 for 2.5" drives (HDD or SSD, SATA).
- Mechanical bays accepting 3.5" and 2.5" drives (3D-printable or off-the-shelf frame).
- Per-bay power control (staggered spin-up, safe power-off).
- Per-bay temperature sensing with fan control and over-temperature cut-off.

## Design principles

- **Deliverables, in order**: a backplane PCB (sized, then manufactured by a PCB fab), then a plastic enclosure around it.
- **No simultaneous spin-up**: drives are powered one at a time, ordered by a per-bay priority. The power supply is sized for the steady-state load plus one spin-up peak, not for 10 simultaneous peaks.

## Inspiration

Commercial 5-bay hot-swap SATA cages that fit three 5.25" drive slots. This project is a DIY take that scales to 10 bays and adds per-bay power and temperature management.

## Toolchain

- **KiCad**: schematics and PCB.
- **PCB trace calculator**: trace width and current sizing for the power paths.
- **PSpice**: simulation of the power-switching and sensing circuits.
- **FreeCAD** or **Fusion 360**: mechanical design of the bays. Fusion 360 depends on the student licence, which is not installed yet; FreeCAD is the default until then.

## Status

Concept phase. See [PROJECT_LOG.md](PROJECT_LOG.md).
