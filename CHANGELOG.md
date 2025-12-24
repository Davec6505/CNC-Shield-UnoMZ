# Changelog

All notable changes to the CNC Shield for UnoMZ project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2025-12-24

### Added
- Initial release of CNC Shield for Arduino UnoMZ project
- Complete project documentation and specifications
- Configurable 4-axis OR 3-axis + spindle control (pins D12/D13 shared)
- Support for A4988, DRV8825, and compatible stepper drivers
- 6 limit switch inputs (2 per axis for X, Y, Z)
- Spindle control interface (enable, direction, PWM in 3-axis mode)
- Coolant control output
- Z-axis probe input for auto-leveling
- Emergency stop input
- Microstepping configuration jumpers for each axis
- Comprehensive documentation:
  - Assembly guide with step-by-step instructions
  - Detailed pinout documentation with configuration modes
  - Bill of Materials (BOM) with component specifications
  - GRBL configuration examples for different machine types
- KiCad starter project files:
  - Project structure and configuration
  - Basic schematic template with component definitions
  - PCB template with board outline (69mm x 54mm)
  - Pin assignments and net definitions
- Gerber file generation documentation
- Contributing guidelines
- MIT License
- Safety warnings and best practices documentation

### Known Limitations
- KiCad files are starter templates - full PCB design needs community completion
- No footprint assignments in schematic yet
- PCB routing not yet complete
- Design not yet physically tested
- Manufacturing Gerber files not yet generated

### Hardware Features
- Arduino Uno shield form factor
- 12-36V DC power input for stepper motors
- 5V logic level compatible
- Screw terminals for easy motor connection
- Pin headers for limit switches and accessories
- Power LED indicator
- Pull-up resistors for limit switches
- Power filtering capacitors for each driver
- Stackable design with Arduino headers

### Documentation
- Complete README with features and specifications
- Detailed assembly guide with safety precautions
- Pin mapping and electrical specifications
- GRBL firmware configuration examples
- Troubleshooting guide
- Calibration procedures
- Example machine configurations

### Project Structure
- Organized directory structure for hardware, documentation, and firmware
- KiCad design files in `hardware/kicad/`
- Bill of Materials in `hardware/bom/`
- Gerber file directory in `hardware/gerber/`
- Documentation in `docs/`
- GRBL configuration examples in `firmware/`

## [Unreleased]

### Planned
- Physical prototype testing and validation
- High-resolution photos of assembled board
- Complete Gerber files for manufacturing
- 3D renders from KiCad
- Video assembly tutorial
- More detailed wiring diagrams
- Support for additional stepper driver types (TMC2208, TMC2209)
- Optional fan control output
- Optional temperature sensor input
- PCB revision based on prototype testing
- Community feedback integration

## Version Numbering

- **Major version** (X.0.0): Incompatible hardware changes
- **Minor version** (1.X.0): New features, backward compatible
- **Patch version** (1.0.X): Bug fixes and documentation updates

## Types of Changes

- **Added**: New features
- **Changed**: Changes to existing functionality
- **Deprecated**: Soon-to-be removed features
- **Removed**: Removed features
- **Fixed**: Bug fixes
- **Security**: Security vulnerability fixes

## Release Notes

### Version 1.0.0 Notes

This is the initial release of the CNC Shield for Arduino UnoMZ. The design is based on the popular CNC Shield V3 but optimized for the UnoMZ platform.

**Key Features:**
- Compatible with standard Arduino shields
- GRBL firmware support
- Easy assembly with through-hole components
- Comprehensive documentation
- Open-source hardware (MIT License)

**Target Applications:**
- CNC routers
- CNC mills
- Laser engravers
- 3D printers (if used with appropriate firmware)
- Pen plotters
- Pick and place machines

**Known Limitations:**
- Design not yet physically tested (prototype phase)
- Gerber files pending final design validation
- No photos of assembled hardware yet
- Firmware examples are generic and may need tuning

**Next Steps:**
- Prototype fabrication
- Hardware testing and validation
- Community feedback collection
- Documentation improvements based on real-world use

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on contributing to this project.

## Links

- [Repository](https://github.com/Davec6505/CNC-Shield-UnoMZ)
- [Issues](https://github.com/Davec6505/CNC-Shield-UnoMZ/issues)
- [Pull Requests](https://github.com/Davec6505/CNC-Shield-UnoMZ/pulls)

---

**Note**: Dates follow ISO 8601 format (YYYY-MM-DD)

[1.0.0]: https://github.com/Davec6505/CNC-Shield-UnoMZ/releases/tag/v1.0.0
[Unreleased]: https://github.com/Davec6505/CNC-Shield-UnoMZ/compare/v1.0.0...HEAD
