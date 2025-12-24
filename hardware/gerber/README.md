# Gerber Files

This directory will contain Gerber files for PCB manufacturing once the design is finalized.

## What are Gerber Files?

Gerber files are the standard format used by PCB manufacturers to produce printed circuit boards. They contain all the information needed to fabricate the PCB layers.

## Typical Gerber File Set

A complete set of Gerber files typically includes:

- **`.GTL`** - Top Copper Layer
- **`.GBL`** - Bottom Copper Layer
- **`.GTO`** - Top Silkscreen (component markings)
- **`.GBO`** - Bottom Silkscreen
- **`.GTS`** - Top Solder Mask
- **`.GBS`** - Bottom Solder Mask
- **`.GTP`** - Top Paste (for SMD components)
- **`.GBP`** - Bottom Paste
- **`.GKO`** or **`.GM1`** - Board Outline
- **`.TXT`** - Drill file (for holes)

## Generating Gerber Files from KiCad

1. Open the PCB file (`CNC-Shield.kicad_pcb`) in KiCad PCBNew
2. Go to **File → Plot**
3. Select output directory (this folder)
4. Check the following layers:
   - F.Cu (Front Copper)
   - B.Cu (Back Copper)
   - F.SilkS (Front Silkscreen)
   - B.SilkS (Back Silkscreen)
   - F.Mask (Front Solder Mask)
   - B.Mask (Back Solder Mask)
   - Edge.Cuts (Board Outline)
5. Set plot format to **Gerber**
6. Click **Plot** button
7. Click **Generate Drill Files** button
8. Generate drill files in Excellon format

## PCB Specifications for Manufacturing

When ordering PCBs, use these specifications:

| Parameter | Value |
|-----------|-------|
| Layers | 2 (Double-sided) |
| Board Thickness | 1.6mm |
| Copper Weight | 1 oz (35 µm) |
| Min Track/Space | 0.2mm / 0.2mm |
| Min Hole Size | 0.3mm |
| Surface Finish | HASL, ENIG, or Lead-Free HASL |
| Solder Mask Color | Green (standard) or other |
| Silkscreen Color | White (standard) |

## Popular PCB Manufacturers

- **JLCPCB** - https://jlcpcb.com (Low cost, good quality)
- **PCBWay** - https://www.pcbway.com (Good service)
- **OSH Park** - https://oshpark.com (USA based)
- **ALLPCB** - https://www.allpcb.com
- **Seeed Studio** - https://www.seeedstudio.com/fusion_pcb.html

## Cost Estimate

Typical costs for prototype quantities:
- 5 PCBs: $10-20 USD
- 10 PCBs: $15-30 USD
- Shipping: $10-20 USD (varies by location)
- Total: ~$25-50 USD for 5-10 boards

Lead time: 7-14 days including shipping

## Assembly Options

Most manufacturers offer assembly services (PCBA):
- Provide BOM (Bill of Materials)
- Provide pick-and-place files
- They source and solder components
- More expensive but saves time

For this shield, through-hole assembly is recommended as it's easier to hand-solder.

## Quality Check

Before manufacturing:
1. Run DRC (Design Rule Check) in KiCad
2. Verify all components have footprints
3. Check board dimensions (69mm x 54mm)
4. Verify mounting holes align with Arduino Uno
5. Review 3D view in KiCad
6. Use online Gerber viewer to inspect files

## File Naming Convention

Standard Gerber file names:
```
CNC-Shield-v1.0-F.Cu.gbr      (Top copper)
CNC-Shield-v1.0-B.Cu.gbr      (Bottom copper)
CNC-Shield-v1.0-F.SilkS.gbr   (Top silkscreen)
CNC-Shield-v1.0-B.SilkS.gbr   (Bottom silkscreen)
CNC-Shield-v1.0-F.Mask.gbr    (Top solder mask)
CNC-Shield-v1.0-B.Mask.gbr    (Bottom solder mask)
CNC-Shield-v1.0-Edge.Cuts.gbr (Board outline)
CNC-Shield-v1.0-PTH.drl       (Plated through holes)
CNC-Shield-v1.0-NPTH.drl      (Non-plated through holes)
```

## Notes

- Always double-check Gerber files before submitting to manufacturer
- Keep backups of your Gerber files
- Most manufacturers accept zipped Gerber files
- Include a text file with any special instructions
- Consider ordering extra boards for testing and mistakes

## Contact

For questions about PCB manufacturing or Gerber generation, please open an issue on GitHub.
