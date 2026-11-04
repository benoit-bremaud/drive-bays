# drive-bays

Hot-swappable bays for 3.5" and 2.5" hard drives, with per-bay power switching and temperature monitoring.

## Goals

- 10 hot-swappable bays: 5 for 3.5" drives and 5 for 2.5" drives (HDD or SSD, SATA).
- Per-bay power control (staggered spin-up, safe power-off).
- Per-bay temperature sensing with fan control and over-temperature cut-off.

## Design principles

- **Architecture**: one 5-bay backplane PCB design, built twice (one module per drive format) and driven by a shared controller, see [ADR-0001](docs/architecture/decisions/0001-build-two-modules-from-one-five-bay-pcb.md).
- **Deliverables, in order**: the backplane PCB (sized, then manufactured by a PCB fab), then one plastic enclosure per drive format.
- **No simultaneous spin-up**: drives are powered one at a time, ordered by a per-bay priority. The power supply is sized for the steady-state load plus one spin-up peak, not for 10 simultaneous peaks. SSDs have no spin-up peak. The 3.3 V SATA rail handling (passed through or switched) is to be decided in the schematic.

## Inspiration

Commercial 5-bay hot-swap SATA cages that fit three 5.25" drive slots. This project is a DIY take that scales to 10 bays and adds per-bay power and temperature management.

## Toolchain

- **KiCad**: schematics and PCB, including its built-in PCB calculator (trace width and current sizing for the power paths) and its ngspice simulator, the Linux path for circuit simulation.
- **PSpice**: simulation of the power-switching and sensing circuits. It runs on Windows only, so it needs a Windows host or VM.
- **FreeCAD** or **Autodesk Fusion**: mechanical design of the bays. Fusion runs on Windows and macOS only and depends on the student licence being granted and the app installed; FreeCAD is the default until then.

## Status

Concept phase. See [PROJECT_LOG.md](PROJECT_LOG.md).
