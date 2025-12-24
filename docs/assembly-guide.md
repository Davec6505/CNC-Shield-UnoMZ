# CNC Shield Assembly Guide

This guide will walk you through assembling and configuring your CNC Shield for the Arduino UnoMZ.

## Table of Contents

1. [Tools and Materials Required](#tools-and-materials-required)
2. [Safety Precautions](#safety-precautions)
3. [PCB Assembly](#pcb-assembly)
4. [Stepper Driver Installation](#stepper-driver-installation)
5. [Microstepping Configuration](#microstepping-configuration)
6. [Wiring Connections](#wiring-connections)
7. [Power Supply Setup](#power-supply-setup)
8. [Testing and Verification](#testing-and-verification)
9. [Troubleshooting](#troubleshooting)

## Tools and Materials Required

### Tools
- Soldering iron (temperature controlled, 300-350°C)
- Solder (60/40 or lead-free)
- Wire strippers
- Small screwdriver set
- Multimeter
- Helping hands or PCB holder
- Desoldering pump or wick (for mistakes)
- Flush cutters
- Safety glasses

### Materials
- CNC Shield PCB (this project)
- All components from BOM
- Arduino UnoMZ board
- 22-24 AWG wire for connections
- Heat shrink tubing
- Cable ties

## Safety Precautions

⚠️ **IMPORTANT SAFETY WARNINGS**

- **Disconnect power** before making any connections or adjustments
- **Check voltage settings** on power supply before connecting
- **Verify polarity** of all connections
- **Use proper ventilation** when soldering
- **Wear safety glasses** when cutting wires or component leads
- **Double-check driver orientation** before powering on
- **Start with low current settings** and increase gradually
- **Install emergency stop** before first operation
- **Never touch moving parts** during operation
- **Keep fingers away** from motor couplings and belts

## PCB Assembly

### Step 1: Component Preparation

1. Organize all components according to the BOM
2. Check PCB for any manufacturing defects
3. Clean PCB with isopropyl alcohol if needed
4. Review schematic and placement diagram

### Step 2: Solder Resistors (R1-R9)

1. Insert resistors through their designated holes
2. Bend leads at 90° to hold in place
3. Solder from the bottom side
4. Trim excess leads with flush cutters
5. Verify correct values with multimeter if needed

**Tip**: Solder resistors first as they have the lowest profile.

### Step 3: Solder Ceramic Capacitors (C5-C8)

1. Insert 100nF ceramic capacitors
2. Polarity doesn't matter for ceramic caps
3. Solder and trim leads

### Step 4: Solder LED (LED1) and Current Limiting Resistor (R9)

1. Note LED polarity (long lead = positive/anode)
2. Insert LED with correct orientation
3. Solder and trim leads

**Note**: Flat side of LED indicates cathode (negative).

### Step 5: Solder Electrolytic Capacitors (C1-C4)

1. **Check polarity** - white stripe indicates negative
2. Insert with correct orientation
3. Solder carefully - they are sensitive to heat
4. Verify polarity before proceeding

### Step 6: Solder Pin Headers

1. **Arduino stacking headers (P1-P4)**: Use female headers
   - Place headers on Arduino first
   - Set shield PCB on top
   - Solder one pin per header first
   - Check alignment
   - Solder remaining pins

2. **Jumper headers (JP1-JP12)**: Male pin headers
   - Insert and solder 3-pin headers for microstepping

3. **Connector headers (J5-J13)**: Male or female as preferred
   - Limit switch connectors: 2-pin headers
   - Probe connector: 2-pin header
   - Spindle connector: 3-pin header
   - Coolant connector: 2-pin header

### Step 7: Solder Stepper Driver Sockets (U1-U4)

1. Use 16-pin IC sockets or female headers
2. Note orientation markings on PCB
3. Solder carefully - these will hold the drivers

**Important**: Ensure sockets are flush with PCB before soldering.

### Step 8: Solder Screw Terminals

1. **Motor connectors (J1-J4)**: 4-pin screw terminals
2. **Power input (J14)**: 2-pin screw terminal
3. Orient opening toward edge of board
4. Solder all pins securely

### Step 9: Final Inspection

1. Check all solder joints for cold joints or bridges
2. Clean flux residue with isopropyl alcohol
3. Verify no shorts with multimeter
4. Check continuity of critical traces

## Stepper Driver Installation

### Step 1: Choose Your Drivers

Common options:
- **A4988**: Budget-friendly, up to 2A, 1/16 microstepping
- **DRV8825**: Better performance, up to 2.5A, 1/32 microstepping
- **TMC2208/2209**: Silent operation, advanced features

### Step 2: Install Heatsinks

1. Clean driver chip surface with alcohol
2. Remove adhesive backing from heatsink
3. Press heatsink firmly onto driver chip
4. Allow adhesive to set for 10 minutes

### Step 3: Set Current Limit (BEFORE INSTALLATION)

**For A4988**:
1. Connect driver to power supply (no motor yet)
2. Measure voltage on Vref pin
3. Calculate current: I = Vref / (8 × Rsense)
4. For Rsense = 0.1Ω: I = Vref / 0.8
5. Adjust potentiometer to desired current

**For DRV8825**:
1. Similar process but formula is: I = Vref / (5 × Rsense)
2. For Rsense = 0.1Ω: I = Vref × 2

**Target Current**: Set to 70-80% of motor rated current.

### Step 4: Install Drivers on Shield

1. **CRITICAL**: Verify driver orientation
   - Check enable pin position
   - Align with markings on PCB
   - GND pins should align with GND on socket

2. **A4988 Orientation**:
   - Potentiometer should face specific direction (check PCB markings)
   - Enable pin typically toward edge

3. **DRV8825 Orientation**:
   - Similar to A4988 but verify pinout
   - Check datasheet if unsure

4. Insert driver carefully into socket
5. Ensure all pins are in socket holes
6. Press down gently until seated

**WARNING**: Incorrect orientation will destroy the driver!

## Microstepping Configuration

### Jumper Settings

Install jumpers under each driver socket according to desired microstepping:

| Microstepping | MS1 | MS2 | MS3 | Smoothness | Speed |
|---------------|-----|-----|-----|------------|-------|
| Full Step | No | No | No | Lowest | Highest |
| 1/2 Step | Yes | No | No | Low | High |
| 1/4 Step | No | Yes | No | Medium | Medium |
| 1/8 Step | Yes | Yes | No | Good | Good |
| 1/16 Step | Yes | Yes | Yes | Highest | Lower |

**Recommendation**: Start with 1/8 or 1/16 for good balance.

### Configuration Example

For typical CNC application:
- **X and Y axes**: 1/8 step (good speed and smoothness)
- **Z axis**: 1/16 step (prioritize precision)
- **A axis**: 1/8 step (balanced)

## Wiring Connections

### Step 1: Mount Shield on Arduino

1. Align all headers carefully
2. Press down evenly on all corners
3. Verify shield is seated completely
4. Check that no pins are bent

### Step 2: Connect Stepper Motors

1. Identify motor coil pairs (measure resistance)
2. Connect to screw terminals:
   ```
   Terminal 1: Coil A+
   Terminal 2: Coil A-
   Terminal 3: Coil B+
   Terminal 4: Coil B-
   ```
3. Tighten screws firmly
4. Use color-coded wires for easier troubleshooting

**Finding Coil Pairs**:
- Measure resistance between wire pairs
- Coil pairs will show 1-10Ω resistance
- Non-pairs will show infinite resistance

### Step 3: Connect Limit Switches

1. Wire limit switches to their respective connectors
2. Typical wiring: Switch → Signal pin, GND → GND
3. Use shielded cable if available
4. Keep limit switch wires away from motor wires

**Switch Type**:
- Normally Open (NO) is standard
- Switch closes when activated
- GRBL default expects NO switches

### Step 4: Connect Spindle (Optional)

1. For relay control: Connect relay to spindle connector
2. For ESC control: Connect signal wire to enable pin
3. Direction pin can control CW/CCW if supported

### Step 5: Connect Probe (Optional)

1. Connect probe to probe connector
2. Typically: Probe tip → Signal, Tool → GND
3. Use shielded cable for noise immunity

### Step 6: Connect Emergency Stop

1. Use normally closed (NC) button
2. Wire in series with power or use abort input
3. Place in easily accessible location

## Power Supply Setup

### Step 1: Calculate Power Requirements

Calculate total power needed:
```
Power = Voltage × (Current per motor × Number of motors)
Example: 24V × (1.5A × 4) = 144W
Add 20% safety margin: 144W × 1.2 = 173W
Choose: 24V 200W power supply
```

### Step 2: Connect Power Supply

1. **Verify voltage setting** on power supply
2. Connect to power input terminals:
   - Red/Positive (+) → V+ terminal
   - Black/Negative (-) → GND terminal
3. Connect Arduino USB or barrel jack separately
4. **Ensure common ground** between shield and Arduino

### Step 3: Power-Up Sequence

1. **Double-check all connections**
2. Remove stepper drivers temporarily
3. Connect power supply
4. Verify 5V present on Arduino
5. Check for short circuits
6. Power off
7. Re-install stepper drivers
8. Power on and test

## Testing and Verification

### Pre-Power Checks

- [ ] All solder joints complete
- [ ] No solder bridges
- [ ] Driver orientation correct
- [ ] Heatsinks installed
- [ ] Current limit set
- [ ] Motor connections secure
- [ ] Power polarity correct
- [ ] Emergency stop functional

### Initial Power-Up

1. Power on with no motors connected
2. Check power LED illuminates
3. Measure voltages with multimeter
4. Verify 5V on logic circuits
5. Check motor supply voltage present

### Motor Test

1. Upload GRBL firmware to Arduino
2. Connect to PC via USB
3. Use terminal program (115200 baud)
4. Test each axis with jog commands
5. Verify direction and movement

### Example GRBL Commands

```
$$ - View settings
$X - Unlock (after startup)
$H - Home (if limit switches installed)
G91 - Relative positioning
G0 X10 - Move X axis 10mm
G0 Y10 - Move Y axis 10mm
G0 Z10 - Move Z axis 10mm
```

## Troubleshooting

### Motor Doesn't Move

- Check enable pin (should be LOW for operation)
- Verify driver installation and orientation
- Check motor connections
- Verify power supply voltage
- Check current limit setting

### Motor Moves in Wrong Direction

- Swap one coil pair wires
- Or invert direction in GRBL settings: `$3=1`

### Motor Stutters or Skips

- Increase current limit
- Check for mechanical binding
- Verify microstepping setting
- Check power supply capacity

### Overheating

- Reduce current limit
- Add better heatsinks
- Improve airflow with fan
- Check for short circuits

### Limit Switches Not Working

- Verify wiring and polarity
- Check GRBL settings: `$5=0` for active low
- Test switch continuity with multimeter
- Check pull-up resistors

### Shield Not Recognized

- Check Arduino connection
- Verify USB cable
- Check that shield is properly seated
- Verify no bent pins

## Next Steps

After successful assembly and testing:

1. Calibrate steps per mm for each axis
2. Set acceleration and max speed
3. Configure homing cycle
4. Test limit switches
5. Set up your CNC software
6. Create test cuts with soft material
7. Fine-tune settings for your machine

## Additional Resources

- GRBL Wiki: https://github.com/gnea/grbl/wiki
- GRBL Settings Guide: https://github.com/gnea/grbl/wiki/Grbl-v1.1-Configuration
- Universal G-Code Sender: https://winder.github.io/ugs_website/
- CNC Community Forums

## Maintenance

Regular maintenance tips:
- Clean dust regularly
- Check wire connections monthly
- Verify current settings
- Replace heatsinks if adhesive fails
- Update firmware as needed
- Keep backup of GRBL settings

---

**Remember**: Take your time during assembly. Double-check every connection before applying power. Safety first!

If you encounter issues not covered here, please open an issue on GitHub or consult the community forums.
