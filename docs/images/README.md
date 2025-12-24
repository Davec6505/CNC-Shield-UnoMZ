# Schematic and Image Files

This directory contains schematics, diagrams, and photos for the CNC Shield project.

## Contents

- **schematic.pdf** - Full schematic diagram (to be generated from KiCad)
- **pcb-layout.pdf** - PCB layout diagram (to be generated from KiCad)
- **pinout-diagram.png** - Visual pinout reference
- **assembly-photos/** - Photos of assembled board
- **connection-diagrams/** - Wiring diagrams for motors, switches, etc.

## Generating Images from KiCad

### Export Schematic as PDF
1. Open `CNC-Shield.kicad_sch` in KiCad Schematic Editor
2. Go to **File → Plot**
3. Select PDF format
4. Choose output directory (this folder)
5. Click **Plot**

### Export PCB as PDF
1. Open `CNC-Shield.kicad_pcb` in KiCad PCBNew
2. Go to **File → Plot**
3. Select PDF format
4. Select all layers you want to include
5. Click **Plot**

### Generate 3D View
1. Open `CNC-Shield.kicad_pcb` in KiCad PCBNew
2. Go to **View → 3D Viewer**
3. Adjust view angle
4. Use **File → Export → PNG** to save image
5. Save to this directory

### Create Pinout Diagram
1. Use drawing software (Inkscape, Adobe Illustrator, etc.)
2. Base on schematic and PCB layout
3. Create clear, labeled diagram showing all connections
4. Export as PNG or PDF
5. Save to this directory

## Photo Guidelines

If contributing photos:
- Use good lighting
- Show clear, focused images
- Include scale reference if helpful
- Annotate important features
- Save in high resolution (at least 1920x1080)
- Use descriptive filenames

## Diagram Guidelines

For connection diagrams:
- Use clear, simple illustrations
- Label all connections
- Use consistent color coding
- Include wire gauge recommendations
- Add safety warnings where appropriate
- Save in vector format (SVG, PDF) when possible

## Placeholder Files

Until actual hardware is produced, this directory may contain:
- Rendered 3D views from KiCad
- Schematic exports
- Generated layout images
- Diagrams created from documentation

## Contributing Images

When contributing images or diagrams:
1. Ensure they are clear and high quality
2. Use descriptive filenames
3. Add appropriate documentation
4. Credit sources if applicable
5. Follow open-source license requirements

## File Naming Convention

```
cnc-shield-schematic-v1.0.pdf
cnc-shield-pcb-top-v1.0.png
cnc-shield-pcb-bottom-v1.0.png
cnc-shield-3d-view-v1.0.png
cnc-shield-assembled-front.jpg
wiring-diagram-motors.png
wiring-diagram-limits.png
pinout-reference.png
```

## Tools for Creating Diagrams

Recommended tools:
- **Inkscape** - Free vector graphics editor
- **GIMP** - Free raster graphics editor
- **Fritzing** - Circuit diagram tool
- **Draw.io** - Online diagram tool
- **KiCad** - PCB design software (included in project)

## License

All images and diagrams are licensed under the same MIT License as the rest of the project, unless otherwise noted.

Images from external sources must be properly attributed and compatible with the MIT License.
