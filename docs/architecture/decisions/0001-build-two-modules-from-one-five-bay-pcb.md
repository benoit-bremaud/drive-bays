# ADR-0001: Build two modules from one five-bay PCB design

- Status: accepted
- Date: 2026-11-04

## Context

The rack holds 10 drives: 5 of 3.5" and 5 of 2.5". The backplane PCB must be sized and manufactured, then enclosed in a plastic housing. Drives never spin up simultaneously; a per-bay priority orders power-on.

## Decision drivers

PCB fabrication cost and risk, power and thermal simplicity, 3D-printing feasibility, maintenance, design effort, scalability, cabling.

## Options considered (MCDA, weights sum to 100, scores 0-5, total /500)

| Option | Total |
|---|---|
| A: 2 modules, 2 format-specific PCBs | 325 |
| B: monolithic enclosure, one 10-bay PCB | 255 |
| C: one 5-bay PCB design built twice, 2 enclosures (one per format), shared controller | 400 |

Scores are estimates: printer bed size, PCB fabrication prices and module dimensions are not yet verified. Sensitivity: C stays first with fabrication cost weighted 10 and design effort 25; B overtakes C only if power and cabling weigh over about 70 %.

## Outcome

Option C. The 5-bay PCB carries 12 V and 5 V switching on every bay so it serves both formats; the 2.5" module leaves its 12 V switches unused.

## Consequences

- One PCB to route, simulate and prototype; identical spare boards.
- A shared controller links the two modules through a bus, to be specified.
- The enclosure is designed per format around the same PCB footprint.
