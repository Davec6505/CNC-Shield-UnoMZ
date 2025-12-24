# CNC Shield for UnoMZ

A CNC Shield expansion board designed for the Arduino UnoMZ, enabling 4-axis CNC machine control with support for stepper motor drivers, limit switches, spindle control, and coolant control.

> **Project Status**: This is an initial release with comprehensive documentation and design specifications. The KiCad PCB files are starter templates. Community contributions to complete the hardware design are welcome!

## Features

- **4-Axis Support**: Control up to 4 stepper motors (X, Y, Z, and A axes)*
- **3-Axis + Spindle Mode**: Standard 3-axis CNC with spindle control*
- **Stepper Driver Compatibility**: Compatible with A4988, DRV8825, and similar drivers
- **Limit Switch Support**: 2 endstops per axis (6 total limit switches)
- **Spindle Control**: Enable, direction, and PWM speed control*
- **Coolant Control**: Dedicated coolant enable output
- **Emergency Stop**: Hardware emergency stop input
- **Probe Input**: Z-axis probe for auto-leveling and tool height measurement
- **Microstepping Configuration**: Jumper-configurable microstepping for each axis
- **GRBL Compatible**: Designed to work with GRBL firmware
- **Power Supply**: 12-36V DC input for stepper motors

*Note: Pins D12 and D13 are shared between A-axis (4th axis) and spindle control. You must choose one mode in firmware configuration. Most CNC routers/mills use 3-axis + spindle mode.

## Pin Mapping

### Core Functions (Always Available)

| Function            | Arduino Pin | Description                    |
|---------------------|-------------|--------------------------------|
| X_STEP              | D2          | X-axis step signal             |
| X_DIR               | D5          | X-axis direction signal        |
| Y_STEP              | D3          | Y-axis step signal             |
| Y_DIR               | D6          | Y-axis direction signal        |
| Z_STEP              | D4          | Z-axis step signal             |
| Z_DIR               | D7          | Z-axis direction signal        |
| STEPPER_ENABLE      | D8          | Enable all stepper drivers     |
| X_LIMIT             | D9          | X-axis limit switch            |
| Y_LIMIT             | D10         | Y-axis limit switch            |
| Z_LIMIT             | D11         | Z-axis limit switch            |
| COOLANT_ENABLE      | A3          | Coolant enable signal          |
| PROBE               | A5          | Z-probe input                  |

### Configuration A: 4-Axis Mode (Default)

| Function            | Arduino Pin | Description                    |
|---------------------|-------------|--------------------------------|
| A_STEP              | D12         | A-axis (4th axis) step signal  |
| A_DIR               | D13         | A-axis direction signal        |

### Configuration B: 3-Axis + Spindle Mode

| Function            | Arduino Pin | Description                    |
|---------------------|-------------|--------------------------------|
| SPINDLE_ENABLE      | D12         | Spindle enable signal          |
| SPINDLE_DIRECTION   | D13         | Spindle direction control      |
| SPINDLE_PWM         | D11         | Spindle speed (PWM - shared with Z_LIMIT) |

**Note**: Pins D12 and D13 are shared between the A-axis (4th axis) and spindle control. You must choose one configuration in your GRBL firmware. Most users will use 3-axis + spindle mode for CNC routers/mills.

## Specifications

- **Board Dimensions**: ~69mm x 54mm (Arduino Uno compatible)
- **Input Voltage**: 12-36V DC (check your stepper driver limits)
- **Logic Level**: 5V (Arduino compatible)
- **Number of Axes**: 3 or 4 (configurable - see pin mapping)
  - Standard Mode: 3 axes (X, Y, Z) + Spindle control
  - Alternative Mode: 4 axes (X, Y, Z, A) - no spindle control
- **Stepper Drivers**: 4 x A4988/DRV8825 compatible sockets
- **Limit Switches**: 6 inputs (X+, X-, Y+, Y-, Z+, Z-)
- **Firmware**: GRBL 1.1 or newer recommended (standard 3-axis + spindle)

## Getting Started

### Hardware Requirements

1. Arduino UnoMZ board
2. CNC Shield PCB (this project)
3. 4x Stepper motor drivers (A4988 or DRV8825)
4. Stepper motors (NEMA 17 or NEMA 23)
5. 12-36V power supply (depending on motors and drivers)
6. Limit switches (optional but recommended)
7. Spindle or router (optional)

### Assembly Instructions

1. **Mount Stepper Drivers**: Insert stepper drivers into the designated sockets, ensuring correct orientation (check driver pinout)
2. **Configure Microstepping**: Set jumpers below each driver socket for desired microstepping resolution
3. **Connect Power**: Connect 12-36V power supply to the power input terminals
4. **Mount Shield**: Stack the shield onto your Arduino UnoMZ
5. **Connect Motors**: Connect stepper motors to the 4-pin motor connectors
6. **Connect Limit Switches**: Connect limit switches to the endstop headers
7. **Connect Spindle**: Connect spindle control signals if using a spindle

### Firmware Setup

1. Install GRBL firmware on your Arduino UnoMZ
2. Configure GRBL settings for your specific machine
3. Use GRBL-compatible software (e.g., Universal G-Code Sender, bCNC, Easel)

```bash
# Example GRBL configuration commands
$0=10    # Step pulse time
$1=25    # Step idle delay
$2=0     # Step pulse invert
$3=0     # Step direction invert
$4=0     # Invert step enable pin
$5=0     # Invert limit pins
```

## Safety Warnings

⚠️ **Important Safety Notes:**

- Always ensure proper grounding and electrical safety
- Never connect/disconnect stepper drivers while powered
- Use appropriate current limiting on stepper drivers
- Install emergency stop switches for safety
- Test limit switches before operation
- Ensure proper ventilation for stepper drivers and power supply
- Follow all local electrical codes and regulations

## Project Structure

```
CNC-Shield-UnoMZ/
├── README.md                 # This file
├── LICENSE                   # MIT License
├── hardware/                 # Hardware design files
│   ├── kicad/               # KiCad project files
│   │   ├── CNC-Shield.kicad_pro
│   │   ├── CNC-Shield.kicad_sch
│   │   └── CNC-Shield.kicad_pcb
│   ├── gerber/              # Gerber files for manufacturing
│   └── bom/                 # Bill of Materials
├── docs/                    # Documentation
│   ├── assembly-guide.md    # Assembly instructions
│   ├── pinout.md           # Detailed pinout information
│   └── images/             # Schematics, diagrams, photos
└── firmware/               # Example firmware configurations
    └── grbl-config.txt     # GRBL configuration examples
```

## Bill of Materials (BOM)

See [hardware/bom/BOM.md](hardware/bom/BOM.md) for a complete list of components needed to build this shield.

## Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for bugs, improvements, or new features.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Based on the popular Arduino CNC Shield V3 design
- Compatible with GRBL firmware
- Designed for the Arduino UnoMZ platform

## Support

For questions, issues, or suggestions:
- Open an issue on GitHub
- Check the documentation in the `docs/` folder
- Refer to GRBL documentation for firmware-related questions

## Version History

- **v1.0.0** (2025-12-24): Initial release
  - 4-axis stepper motor control
  - GRBL compatible
  - UnoMZ board support