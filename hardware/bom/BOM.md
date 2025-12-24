# Bill of Materials (BOM)

## CNC Shield for UnoMZ - Component List

### Main Components

| Ref | Qty | Value/Part Number | Description | Package | Notes |
|-----|-----|-------------------|-------------|---------|-------|
| U1-U4 | 4 | Stepper Driver Socket | 16-pin socket for A4988/DRV8825 | 16-pin 2.54mm | For stepper motor drivers |
| J1-J4 | 4 | Motor Connector | 4-pin screw terminal | 5.08mm pitch | For stepper motor connections |
| J5-J10 | 6 | Limit Switch Connector | 2-pin header | 2.54mm pitch | For endstop switches |
| J11 | 1 | Probe Connector | 2-pin header | 2.54mm pitch | For Z-probe input |
| J12 | 1 | Spindle Connector | 3-pin header | 2.54mm pitch | Enable, Direction, PWM |
| J13 | 1 | Coolant Connector | 2-pin header | 2.54mm pitch | Coolant enable |
| J14 | 1 | Power Input | 2-pin screw terminal | 5.08mm pitch | 12-36V DC input |
| J15 | 1 | Emergency Stop | 2-pin header | 2.54mm pitch | E-stop input |

### Arduino Headers

| Ref | Qty | Value | Description | Package |
|-----|-----|-------|-------------|---------|
| P1 | 1 | Arduino Header 8-pin | Digital pins 0-7 | 8-pin female header 2.54mm |
| P2 | 1 | Arduino Header 10-pin | Digital pins 8-13, GND, AREF | 10-pin female header 2.54mm |
| P3 | 1 | Arduino Header 8-pin | Analog pins A0-A5, Power | 8-pin female header 2.54mm |
| P4 | 1 | Arduino Header 8-pin | Power, Reset, IOREF | 8-pin female header 2.54mm |

### Microstepping Jumpers

| Ref | Qty | Value | Description | Package | Notes |
|-----|-----|-------|-------------|---------|-------|
| JP1-JP12 | 12 | Jumper Header | 3x microstepping jumpers per driver | 2.54mm pin header | For microstepping configuration |

### Passive Components

| Ref | Qty | Value | Description | Package | Notes |
|-----|-----|-------|-------------|---------|-------|
| C1-C4 | 4 | 100µF | Electrolytic capacitor | Radial 6.3x11mm | Power filtering for each driver |
| C5-C8 | 4 | 100nF | Ceramic capacitor | 0805 or through-hole | Decoupling for each driver |
| R1-R6 | 6 | 10kΩ | Pull-up resistor | 0805 or 1/4W | For limit switches |
| R7 | 1 | 10kΩ | Pull-up resistor | 0805 or 1/4W | For probe input |
| R8 | 1 | 10kΩ | Pull-up resistor | 0805 or 1/4W | For emergency stop |
| LED1 | 1 | Red LED | Power indicator | 3mm or 5mm | Power on indicator |
| R9 | 1 | 1kΩ | Current limiting resistor | 0805 or 1/4W | For power LED |

### Mounting Hardware

| Ref | Qty | Value | Description | Notes |
|-----|-----|-------|-------------|-------|
| - | 4 | M3x10mm | Mounting screws | For PCB mounting |
| - | 4 | M3 | Standoffs or spacers | 10mm height recommended |

## Stepper Drivers (Not Included)

| Type | Description | Voltage | Current | Microstepping |
|------|-------------|---------|---------|---------------|
| A4988 | Basic stepper driver | Up to 35V | Up to 2A | Up to 1/16 |
| DRV8825 | Advanced stepper driver | Up to 45V | Up to 2.5A | Up to 1/32 |
| TMC2208 | Silent stepper driver | Up to 36V | Up to 2A | Up to 1/256 |
| TMC2209 | Advanced silent driver | Up to 29V | Up to 2A | Up to 1/256 |

## Optional Components

| Item | Description | Notes |
|------|-------------|-------|
| Heatsinks | For stepper drivers | Recommended for continuous operation |
| Cooling Fan | 5V or 12V fan | For better cooling |
| Emergency Stop Button | Normally closed switch | For safety |
| Limit Switches | Mechanical or optical | 6 switches for full homing |
| Power Supply | 12-36V DC | Size based on motor requirements |

## Estimated Costs

- PCB (prototype): $10-20 (depends on quantity and manufacturer)
- Components: $15-25
- Stepper Drivers (4x): $10-40 (depends on type)
- **Total (excluding motors and power supply): $35-85**

## Suppliers

Common suppliers for components:
- Mouser Electronics
- Digikey
- LCSC
- AliExpress (for budget options)
- Amazon
- Local electronics stores

## Notes

1. Choose stepper drivers based on your motor specifications
2. Ensure power supply can handle total current requirements
3. Add heatsinks to drivers for better thermal management
4. Consider using higher quality capacitors for power filtering
5. TMC drivers provide quieter operation but cost more
6. Always verify component values before ordering
