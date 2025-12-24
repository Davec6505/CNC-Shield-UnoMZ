# CNC Shield Pinout Documentation

## Arduino UnoMZ to CNC Shield Pin Mapping

### Core Digital Pins (Always Available)

| Arduino Pin | CNC Function | Type | Description |
|-------------|--------------|------|-------------|
| D0 | RX | UART | Serial receive (reserved for communication) |
| D1 | TX | UART | Serial transmit (reserved for communication) |
| D2 | X_STEP | OUTPUT | X-axis stepper step pulse |
| D3 | Y_STEP | OUTPUT | Y-axis stepper step pulse |
| D4 | Z_STEP | OUTPUT | Z-axis stepper step pulse |
| D5 | X_DIR | OUTPUT | X-axis stepper direction |
| D6 | Y_DIR | OUTPUT | Y-axis stepper direction |
| D7 | Z_DIR | OUTPUT | Z-axis stepper direction |
| D8 | STEPPER_ENABLE | OUTPUT | Enable/disable all stepper drivers (active low) |
| D9 | X_LIMIT | INPUT | X-axis limit switch input |
| D10 | Y_LIMIT | INPUT | Y-axis limit switch input |
| D11 | Z_LIMIT | INPUT | Z-axis limit switch input |

### Configurable Digital Pins (Choose One Configuration)

**Configuration A: 4-Axis Mode**

| Arduino Pin | CNC Function | Type | Description |
|-------------|--------------|------|-------------|
| D12 | A_STEP | OUTPUT | A-axis (4th axis) stepper step pulse |
| D13 | A_DIR | OUTPUT | A-axis stepper direction |

**Configuration B: 3-Axis + Spindle Mode (Most Common)**

| Arduino Pin | CNC Function | Type | Description |
|-------------|--------------|------|-------------|
| D12 | SPINDLE_ENABLE | OUTPUT | Spindle enable signal |
| D13 | SPINDLE_DIRECTION | OUTPUT | Spindle direction control |
| D11 | SPINDLE_PWM | OUTPUT | Spindle speed control (shared with Z_LIMIT) |

**Important**: D12 and D13 are shared between A-axis and spindle functions. You cannot use both simultaneously. Configure in GRBL firmware based on your machine requirements.

### Analog Pins

| Arduino Pin | CNC Function | Type | Description |
|-------------|--------------|------|-------------|
| A0 | ABORT/RESET | INPUT | Emergency stop/reset input |
| A1 | FEED_HOLD | INPUT | Feed hold button input |
| A2 | CYCLE_START | INPUT | Cycle start button input |
| A3 | COOLANT | OUTPUT | Coolant enable output |
| A4 | SDA | I2C | I2C data (available for expansion) |
| A5 | SCL | I2C | I2C clock (available for expansion) / Probe input |

### Power Pins

| Pin | Function | Description |
|-----|----------|-------------|
| VIN | Power Input | Raw DC input voltage from Arduino |
| 5V | 5V Supply | Regulated 5V from Arduino |
| 3.3V | 3.3V Supply | Regulated 3.3V from Arduino |
| GND | Ground | Common ground reference |
| IOREF | I/O Reference | Reference voltage for I/O (5V on UnoMZ) |

## Stepper Driver Pinout

Each stepper driver socket (U1-U4) has the following pins:

| Pin | Name | Description |
|-----|------|-------------|
| 1 | ENABLE | Enable driver (active low) |
| 2 | MS1 | Microstep select 1 |
| 3 | MS2 | Microstep select 2 |
| 4 | MS3 | Microstep select 3 |
| 5 | RESET | Reset (tied to SLEEP for A4988) |
| 6 | SLEEP | Sleep mode control |
| 7 | STEP | Step pulse input |
| 8 | DIR | Direction control |
| 9-10 | GND | Ground |
| 11-12 | VDD | Motor power supply (+12V to +36V) |
| 13-14 | 1A, 1B | Motor coil A |
| 15-16 | 2A, 2B | Motor coil B |

### Microstepping Jumper Configuration

Each axis has three jumpers (MS1, MS2, MS3) to configure microstepping:

#### A4988 Driver Microstepping

| MS1 | MS2 | MS3 | Microstep Resolution |
|-----|-----|-----|---------------------|
| Low | Low | Low | Full step |
| High | Low | Low | Half step (1/2) |
| Low | High | Low | Quarter step (1/4) |
| High | High | Low | Eighth step (1/8) |
| High | High | High | Sixteenth step (1/16) |

#### DRV8825 Driver Microstepping

| MS1 | MS2 | MS3 | Microstep Resolution |
|-----|-----|-----|---------------------|
| Low | Low | Low | Full step |
| High | Low | Low | Half step (1/2) |
| Low | High | Low | Quarter step (1/4) |
| High | High | Low | Eighth step (1/8) |
| Low | Low | High | Sixteenth step (1/16) |
| High | Low | High | 1/32 step |

## Connector Pinouts

### Motor Connectors (J1-J4)

4-pin screw terminals for each axis:

| Pin | Function | Wire Color (typical) |
|-----|----------|---------------------|
| 1 | Motor Coil A+ | Red |
| 2 | Motor Coil A- | Blue |
| 3 | Motor Coil B+ | Green |
| 4 | Motor Coil B- | Black |

### Limit Switch Connectors (J5-J10)

2-pin headers for each limit switch:

| Pin | Function |
|-----|----------|
| 1 | Signal |
| 2 | GND |

Limit switches should be normally open (NO) and close when triggered.

### Spindle Control Connector (J12)

3-pin header:

| Pin | Function | Description |
|-----|----------|-------------|
| 1 | ENABLE | Spindle enable (D12) |
| 2 | DIRECTION | Spindle direction (D13) |
| 3 | GND | Ground reference |

### Probe Connector (J11)

2-pin header:

| Pin | Function |
|-----|----------|
| 1 | PROBE | Probe signal (A5) |
| 2 | GND | Ground reference |

### Coolant Connector (J13)

2-pin header:

| Pin | Function |
|-----|----------|
| 1 | COOLANT | Coolant enable (A3) |
| 2 | GND | Ground reference |

### Power Input (J14)

2-pin screw terminal:

| Pin | Function | Voltage Range |
|-----|----------|---------------|
| 1 | V+ | +12V to +36V DC |
| 2 | GND | Ground |

**Note**: Connect power supply ground to Arduino ground for common reference.

## GRBL Pin Assignments

### Configuration A: 3-Axis + Spindle (Standard GRBL v1.1)

```
// Stepper motors
#define X_STEP_BIT    2  // D2
#define Y_STEP_BIT    3  // D3
#define Z_STEP_BIT    4  // D4
#define X_DIRECTION_BIT   5  // D5
#define Y_DIRECTION_BIT   6  // D6
#define Z_DIRECTION_BIT   7  // D7
#define STEPPERS_DISABLE_BIT 8  // D8

// Limit switches
#define X_LIMIT_BIT   9   // D9
#define Y_LIMIT_BIT   10  // D10
#define Z_LIMIT_BIT   11  // D11

// Spindle control (3-axis mode)
#define SPINDLE_ENABLE_BIT    12  // D12
#define SPINDLE_DIRECTION_BIT 13  // D13
#define SPINDLE_PWM_BIT       11  // D11 (PWM output on OC2A)

// Coolant
#define COOLANT_FLOOD_BIT  A3  // A3

// Probe
#define PROBE_BIT  A5  // A5

// Control signals
#define RESET_BIT       A0  // A0
#define FEED_HOLD_BIT   A1  // A1
#define CYCLE_START_BIT A2  // A2
```

**Note**: In 3-axis + spindle mode, D11 is shared between Z limit switch and spindle PWM. When using variable speed spindle control, you cannot use the Z limit switch on D11. Consider using only Z+ or Z- limit switch, or disable PWM spindle control if you need both Z limit switches.

### Configuration B: 4-Axis Mode (GRBL Mega or Custom)

```
// Stepper motors (4 axes)
#define X_STEP_BIT    2  // D2
#define Y_STEP_BIT    3  // D3
#define Z_STEP_BIT    4  // D4
#define A_STEP_BIT    12 // D12 (4th axis)
#define X_DIRECTION_BIT   5  // D5
#define Y_DIRECTION_BIT   6  // D6
#define Z_DIRECTION_BIT   7  // D7
#define A_DIRECTION_BIT   13 // D13 (4th axis)
#define STEPPERS_DISABLE_BIT 8  // D8

// Limit switches
#define X_LIMIT_BIT   9   // D9
#define Y_LIMIT_BIT   10  // D10
#define Z_LIMIT_BIT   11  // D11

// Coolant
#define COOLANT_FLOOD_BIT  A3  // A3

// Probe
#define PROBE_BIT  A5  // A5

// Control signals
#define RESET_BIT       A0  // A0
#define FEED_HOLD_BIT   A1  // A1
#define CYCLE_START_BIT A2  // A2
```

**Note**: Standard GRBL v1.1 does not support 4-axis on Arduino Uno. You need GRBL-Mega or a custom GRBL build for 4-axis support. In this mode, spindle control is not available.

## Electrical Specifications

| Parameter | Min | Typical | Max | Unit |
|-----------|-----|---------|-----|------|
| Logic Supply Voltage | 4.5 | 5.0 | 5.5 | V |
| Motor Supply Voltage | 12 | 24 | 36 | V |
| Logic Input High | 3.0 | 5.0 | 5.5 | V |
| Logic Input Low | 0 | 0 | 1.5 | V |
| Logic Output High | 4.0 | 5.0 | - | V |
| Logic Output Low | - | 0 | 0.5 | V |
| Pull-up Resistor | - | 10 | - | kΩ |

## Safety and Wiring Notes

1. **Always power off before connecting/disconnecting drivers**
2. **Check driver orientation** - incorrect insertion can damage drivers
3. **Set current limit** - adjust driver potentiometer for motor current
4. **Use appropriate wire gauge** - 18-22 AWG for motors
5. **Add capacitors** - 100µF electrolytic near power input
6. **Ground properly** - ensure common ground between shield and power supply
7. **Heat management** - use heatsinks and ensure airflow
8. **Limit switches** - use shielded cable to reduce noise
9. **Emergency stop** - always implement a hardware E-stop

## Troubleshooting Pin Issues

| Problem | Check |
|---------|-------|
| Motors not moving | Enable pin state (should be LOW), driver power, connections |
| Wrong direction | Direction pin polarity, swap motor wires |
| Stuttering/skipping | Current setting, microstepping config, power supply |
| Limit switches not working | Pull-up resistors, switch wiring, GRBL config |
| Spindle not responding | Pin assignments, relay/ESC connections |

## References

- Arduino UnoMZ Pinout
- GRBL v1.1 Documentation
- A4988 Datasheet
- DRV8825 Datasheet
