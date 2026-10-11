# Starbie --- ESP32-C3 Interactive Electronic Pet

Starbie is a small, interactive electronic-pet project built around the
**Seeed Studio XIAO ESP32-C3**. It combines a display, motion sensing,
temperature/humidity sensing, and push buttons to create the foundation
for a responsive desk companion.

> **Project status:** Learning / prototype project. Confirm the final
> wiring, component variants, and firmware behavior against your own
> build before powering or assembling the PCB.

## PCB 3D Preview

![Starbie PCB 3D render](starbie-pcb-render.png)

## Features

-   **OLED display** --- provides a visual interface for the pet.
-   **MPU6050 motion sensor** --- supplies accelerometer and gyroscope
    data for motion-aware interactions.
-   **DHT11 sensor** --- measures ambient temperature and humidity.
-   **Two push buttons** --- provide physical inputs for user
    interaction.
-   **XIAO ESP32-C3** --- compact microcontroller board with Wi-Fi and
    Bluetooth LE capability.
-   **Custom PCB design** --- brings the modules and connections
    together in a compact layout.

## Hardware

The design shown in the project schematic uses the following parts:

  Component                         Purpose
  --------------------------------- ----------------------------------------------------
  Seeed Studio XIAO ESP32-C3        Main microcontroller
  0.96-inch I²C OLED module         Display
  MPU6050 module                    Motion sensing
  DHT11 module                      Temperature and humidity sensing
  2 × momentary push buttons        User input
  10 kΩ resistor                    DHT11 data-line pull-up, as shown in the schematic
  Custom PCB and suitable headers   Mounting and interconnection

Check the exact pinout and voltage requirements of your own modules. The
table above describes the project design, not a guarantee that every
module sold under these names has identical pin labeling.

## Pin mapping

The following mapping is based on the Starbie schematic used during PCB
design.

  Function / signal              XIAO ESP32-C3 connection
  ------------------------------ --------------------------
  DHT11 data                     D1
  Button 1                       D2 / GPIO2
  Button 2                       D3 / GPIO3
  I²C SCL --- OLED and MPU6050   D4
  I²C SDA --- OLED and MPU6050   D5
  Module supply                  3V3
  Ground                         GND

The OLED connector is a 4-pin I²C connection: **GND, SCL, SDA, and 3.3
V**. The MPU6050 connector uses its power, ground, SCL, and SDA pins;
unused connector pins should remain unconnected unless your specific
module requires otherwise.

**Important:** Verify the XIAO ESP32-C3 pin names against the board
documentation and your schematic before wiring. Do not connect a 5 V
signal to a 3.3 V GPIO.

## How the system fits together

1.  The XIAO ESP32-C3 runs the Starbie firmware.
2.  The OLED receives display data over I²C.
3.  The MPU6050 sends motion measurements over the same I²C bus.
4.  The DHT11 sends temperature/humidity readings through its data pin.
5.  The two push buttons provide input to the microcontroller.
6.  The firmware can use these inputs to update the pet's display and
    behavior.

The exact animations, interaction logic, and sensor update intervals
depend on the firmware version you implement.

## PCB design

The PCB is designed in **KiCad**. The schematic defines the electrical
connections, while the PCB editor assigns footprints and routes copper
tracks.

Before manufacturing, run KiCad's **Electrical Rules Checker (ERC)** and
**Design Rules Checker (DRC)**, then review all remaining issues. In
particular:

-   Ensure the board outline is a single, closed shape on `Edge.Cuts`.
-   Use footprints that match the real OLED, sensor modules, buttons,
    resistor, and XIAO board.
-   Check connector pin order and module orientation against their
    datasheets.
-   Confirm copper clearances, solder-mask openings, courtyard
    boundaries, and mounting-hole positions.
-   Verify that all required nets are connected and that no unintended
    tracks remain.
-   Inspect the PCB in 3D view and compare it with the physical parts
    before ordering.

A clean DRC report is helpful, but it does not replace checking the
schematic, footprints, and real-world dimensions.

## Getting started

1.  **Review the project guide:** Read the [Starbie Week 1
    Guide](https://github.com/SharKingStudios/Starbie/blob/main/Week%201%20Guide.md).
2.  **Prepare the hardware:** Gather the XIAO ESP32-C3, OLED, MPU6050,
    DHT11, buttons, resistor, and suitable connectors.
3.  **Review the schematic:** Confirm the pin mapping and supply
    connections before assembling anything.
4.  **Set up the PCB in KiCad:** Assign the correct footprints, arrange
    the parts, route the tracks, and run ERC/DRC.
5.  **Prepare the firmware:** Install the toolchain and libraries
    required by the firmware you choose to use.
6.  **Test modules individually:** Check the OLED, MPU6050, DHT11, and
    buttons one at a time before testing the complete system.
7.  **Integrate and test:** Confirm sensor readings, button responses,
    and display behavior, then document any changes.

This README does not assume a specific firmware framework or library
version. Add the exact Arduino IDE, PlatformIO, or other setup
instructions once your firmware environment is finalized.

## Repository contents

Keep the repository organized so another person can reproduce the build.
For example:

``` text
Starbie/
├── README.md
├── hardware/
│   ├── schematic/
│   └── pcb/
├── firmware/
└── docs/
```

This is a suggested layout, not a description of files already present
in the repository. Adjust it to match your actual project files.

## Troubleshooting

-   **OLED remains blank:** Check 3.3 V, GND, SDA/SCL order, the I²C
    address, and display initialization.
-   **MPU6050 is not detected:** Check its power, shared I²C wiring, and
    the address/configuration of your module.
-   **DHT11 returns invalid readings:** Check the data connection,
    pull-up arrangement, sensor timing, and library configuration.
-   **Buttons do not respond:** Check GPIO assignments, ground
    connections, and whether the firmware uses internal or external
    pull-ups.
-   **PCB DRC errors remain:** Open each violation and inspect the
    referenced footprint or track; do not simply ignore errors without
    understanding them.

## Safety and build notes

-   Disconnect power before changing wiring.
-   Check polarity and pin order before connecting modules.
-   Use only the supply voltage supported by each component.
-   Test the circuit on a safe, current-limited supply where possible.
-   Do not order a PCB until the schematic, footprints, dimensions, and
    DRC results have been reviewed.

## Credits and references

-   **Starbie project guide:** [SharKingStudios/Starbie --- Week 1
    Guide](https://github.com/SharKingStudios/Starbie/blob/main/Week%201%20Guide.md)
-   **Microcontroller:** [Seeed Studio XIAO ESP32-C3
    documentation](https://wiki.seeedstudio.com/XIAO_ESP32C3_Getting_Started/)
-   **PCB design software:** [KiCad
    documentation](https://docs.kicad.org/)

## License

Add the license that applies to your project and any files you create.
Do not assume that third-party symbols, footprints, firmware, or
reference designs use the same license as your own work.
