# Hardware Design Files

This directory contains all hardware design files for the CNC Shield for Arduino UnoMZ.

## Current Status

⚠️ **Project Stage**: Initial Release / Design Phase

The KiCad files provided are **starter templates** with the basic project structure. The complete PCB design with full schematic, routing, and footprints is intended to be developed by the community or in future releases.

**What's Included:**
- KiCad project structure and configuration
- Basic component definitions (Arduino headers, stepper drivers, connectors)
- Board outline and dimensions
- Pin assignments and net definitions

**What's Needed for Manufacturing:**
- Complete schematic with all connections
- Footprint assignments for all components
- Full PCB routing (traces, vias, copper pours)
- Design Rule Check (DRC) validation
- Final Gerber file generation

Community contributions to complete the PCB design are welcome! See [CONTRIBUTING.md](../CONTRIBUTING.md).

## Directory Structure

```
hardware/
├── kicad/              # KiCad design files
│   ├── CNC-Shield.kicad_pro   # KiCad project file
│   ├── CNC-Shield.kicad_sch   # Schematic design
│   └── CNC-Shield.kicad_pcb   # PCB layout
├── gerber/             # Gerber files for manufacturing
│   └── README.md       # Instructions for generating Gerber files
├── bom/                # Bill of Materials
│   └── BOM.md          # Component list with specifications
└── README.md           # This file
```

## KiCad Files

The design is created using KiCad, a free and open-source PCB design software.

### Opening the Project

1. Install KiCad (version 6.0 or later recommended)
   - Download from: https://www.kicad.org/download/

2. Open the project file:
   - Navigate to `hardware/kicad/`
   - Open `CNC-Shield.kicad_pro`

3. View or edit:
   - **Schematic**: Double-click `CNC-Shield.kicad_sch` or click schematic editor icon
   - **PCB Layout**: Double-click `CNC-Shield.kicad_pcb` or click PCB editor icon

### Design Overview

**Board Specifications:**
- **Size**: 69mm x 54mm (Arduino Uno shield standard)
- **Layers**: 2 (double-sided)
- **Copper Thickness**: 1 oz (35 µm)
- **Board Thickness**: 1.6mm
- **Min Track Width**: 0.25mm (0.5mm+ for power)
- **Min Clearance**: 0.2mm
- **Min Hole Size**: 0.3mm

**Key Components:**
- 4x Stepper driver sockets (16-pin)
- 4x Motor screw terminals (4-pin)
- 6x Limit switch headers (2-pin)
- 4x Arduino stacking headers
- Microstepping jumper headers
- Power input terminal
- Control signal headers

### Schematic Organization

The schematic is organized into functional blocks:

1. **Arduino Interface**
   - Stacking headers (P1-P4)
   - Pin assignments

2. **Stepper Drivers**
   - 4x driver sockets (U1-U4)
   - Microstepping jumpers
   - Enable/disable control

3. **Motor Connections**
   - 4x screw terminals (J1-J4)
   - Power distribution

4. **Limit Switches**
   - 6x switch inputs (J5-J10)
   - Pull-up resistors

5. **Spindle Control**
   - Enable, direction, PWM signals
   - Connector (J12)

6. **Probe and Coolant**
   - Probe input (J11)
   - Coolant output (J13)

7. **Power Supply**
   - 12-36V input (J14)
   - Filtering capacitors

### PCB Layout

**Layer Stack:**
- Top Copper (F.Cu): Signal traces, power
- Top Silkscreen (F.SilkS): Component labels, markings
- Top Solder Mask (F.Mask): Solder mask coverage
- Bottom Copper (B.Cu): Ground plane, return paths
- Bottom Silkscreen (B.SilkS): Identification text
- Bottom Solder Mask (B.Mask): Solder mask coverage
- Edge Cuts: Board outline

**Design Rules:**
- Power traces: 1.0mm width minimum
- Signal traces: 0.25mm width
- Ground pour on bottom layer
- Thermal reliefs for through-hole pads
- Via stitching for EMI reduction

### Modifying the Design

If you want to modify the design:

1. **Backup First**: Make a copy of the project
2. **Edit Schematic**: Make changes in schematic editor
3. **Update PCB**: Use "Update PCB from Schematic" tool
4. **Run DRC**: Check for design rule violations
5. **Verify 3D**: View in 3D viewer to check clearances
6. **Document Changes**: Update version and changelog

### Design Rules Check (DRC)

Before manufacturing, always run DRC:

1. Open PCB in PCBNew
2. Click **Inspect → Design Rules Checker**
3. Click **Run DRC**
4. Fix any errors or violations
5. Re-run until clean

## Gerber Files

See `gerber/README.md` for instructions on generating manufacturing files.

Manufacturing files needed:
- Gerber files (various layers)
- Excellon drill files
- Pick-and-place file (optional)
- Bill of Materials (BOM)

## Bill of Materials

See `bom/BOM.md` for complete component list.

The BOM includes:
- Component reference designators
- Part values and specifications
- Package types
- Quantity needed
- Estimated costs
- Supplier information

## Design Considerations

### Power Distribution

- Separate power input for stepper motors (12-36V)
- Arduino provides 5V logic power
- Common ground between all supplies
- Large electrolytic caps for filtering
- Ceramic caps for high-frequency filtering

### Signal Routing

- Keep motor driver traces short
- Separate analog and digital grounds
- Shield limit switch signals from noise
- Use ground pour for EMI reduction
- Avoid routing under drivers (heat)

### Thermal Management

- Driver sockets positioned for airflow
- Space for heatsinks on drivers
- Optional fan mounting holes
- Thermal reliefs on power pads

### Mechanical Design

- Mounting holes at Arduino standard positions
- Clearance for USB and power connectors
- Component height considerations
- Clearance for motor wires

## Version Control

Track design changes:
- Use git for version control
- Tag releases (v1.0, v1.1, etc.)
- Document changes in CHANGELOG.md
- Keep old versions for reference

## Testing and Validation

Before releasing new version:

1. **Design Review**: Check schematic and layout
2. **DRC Pass**: No design rule violations
3. **ERC Pass**: No electrical rule violations
4. **3D Check**: Verify component clearances
5. **Peer Review**: Have someone else check
6. **Prototype**: Build and test physical board
7. **Validation**: Test all functions
8. **Documentation**: Update all docs

## Manufacturing

### Prototype Quantities

For prototypes (1-10 boards):
- Use online PCB services (JLCPCB, PCBWay, etc.)
- 2-layer board is economical
- Through-hole assembly easier for prototypes
- Allow 1-2 weeks for delivery

### Production Quantities

For larger quantities (100+):
- Consider assembly service (PCBA)
- Request quotes from multiple manufacturers
- Verify all components available
- Plan for lead times
- Quality control testing

## Support Files

Additional files that may be needed:

- **3D Models**: STEP files for mechanical design
- **Assembly Drawings**: Component placement guide
- **Test Procedures**: Quality control checklist
- **User Manual**: End-user documentation

## Licensing

All hardware design files are licensed under the MIT License.

You are free to:
- Use commercially
- Modify the design
- Distribute copies
- Sublicense

Requirements:
- Include original copyright notice
- Include license text
- Provide attribution

## Contributing

See [CONTRIBUTING.md](../CONTRIBUTING.md) for guidelines on contributing to the hardware design.

## Resources

### KiCad Resources
- Official Documentation: https://docs.kicad.org/
- Getting Started: https://docs.kicad.org/master/en/getting_started_in_kicad/
- Symbol and Footprint Libraries: https://kicad.github.io/

### PCB Design Resources
- PCB Design Tutorial: https://www.alternatezone.com/electronics/pcb-design/
- High Speed PCB Design: https://www.alternatezone.com/electronics/files/PCBDesignTutorialRevA.pdf
- IPC Standards: https://www.ipc.org/

### Arduino Resources
- Arduino Hardware Design Guide: https://www.arduino.cc/en/Main/Policy
- Shield Design Guide: https://www.arduino.cc/en/Reference/shields

## Contact

For questions about the hardware design:
- Open an issue on GitHub
- Check existing documentation
- Consult KiCad community forums

---

**Last Updated**: 2025-12-24
**Design Version**: 1.0
**KiCad Version**: 6.0 or later
