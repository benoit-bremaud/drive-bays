# ADR-0001: Build two modules from one five-bay PCB design

- Status: accepted
- Date: 2026-11-04

## Context

The rack holds 10 drives: 5 of 3.5" and 5 of 2.5". The backplane PCB must be sized and manufactured, then enclosed in a plastic housing. Drives never spin up simultaneously; a per-bay priority orders power-on.

## Decision drivers

PCB fabrication cost and risk, power and thermal simplicity, 3D-printing feasibility, maintenance, design effort, scalability, cabling.

## Options considered (MCDA, weights sum to 100, scores 0-5, total /500)

- **A**: 2 modules (3.5" and 2.5"), each with its own PCB design.
- **B**: monolithic enclosure, one 10-bay PCB.
- **C**: one 5-bay PCB design built twice, 2 enclosures (one per format), shared controller.

| Criterion | Weight | A | B | C |
|---|---|---|---|---|
| PCB fabrication cost and risk | 20 | 3: two designs, small boards | 2: large dense board, one error scraps everything | 4: one design, one prototype, identical boards |
| Power and thermal simplicity | 15 | 3: two feeds, one control bus | 4: one rail to distribute | 3: same as A |
| Mechanical feasibility (3D printing) | 15 | 4: small parts | 2: parts larger than a printer bed, mixed formats | 4: small parts |
| Maintenance and service | 15 | 4: swap one module | 2: dismantle the whole rack | 5: spare module and board are identical |
| Design effort | 15 | 2: two PCBs to route | 3: one complex PCB | 4: one PCB to route |
| Scalability and reuse | 10 | 4 | 1 | 5: add a 5-bay module |
| Data and power cabling | 10 | 3 | 4 | 3 |
| **Total /500** | **100** | **325** | **255** | **400** |

Points: A = 60+45+60+60+30+40+30; B = 40+60+30+30+45+10+40; C = 80+45+60+75+60+50+30.

Scores are estimates: printer bed size, PCB fabrication prices and module dimensions are not yet verified. The owner validated the weights on 2026-11-04.

Sensitivity: with fabrication cost weighted 10 and design effort 25 (other weights unchanged), the totals become A 315, B 265, C 400, so C stays first. B would overtake C only if power and cabling together weighed roughly 70 % or more of the total (rough estimate).

### Fallback

A (325/500) is the design fallback. It is second because it needs two PCB designs to route and prototype. Activating it is a design change, not a drop-in: the single 5-bay PCB is replaced by two format-specific boards, and the enclosures follow.

## Outcome

Option C. The 5-bay PCB carries 12 V and 5 V switching on every bay so it serves both formats; the 2.5" module leaves its 12 V switches unused.

## Consequences

- One PCB to route, simulate and prototype; identical spare boards.
- A shared controller links the two modules through a bus, to be specified.
- The enclosure is designed per format around the same PCB footprint.
- The 2.5" module inherits the 3.5" bay pitch, so it ends up about as large as the 3.5" module. The SATA connector sits at a different position on 2.5" and 3.5" drives, so the trays or guides of each format must align the drive to the shared connector position (to be checked against the drive form-factor specifications).
