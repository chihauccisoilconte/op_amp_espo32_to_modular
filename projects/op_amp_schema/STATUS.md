# Project status

Updated: 2026-09-28

- Added README.md describing the intended ESP32 DAC-to-modular-synth audio interface and the amplifier shown in the reference image.
- Renamed Untitled.png to schematic.png and linked it from the README.
- Retained the existing Eurorack_audio_amp_BOM.xlsx without changes.
- Checked the image visually and calculated the ideal gain from the displayed resistor values (−33 kΩ / 10 kΩ = −3.3). No circuit edits, simulation, ERC/DRC, datasheet validation, or hardware tests were performed.
- Open decisions: ESP32 model and DAC range, target audio level, DC-offset handling, power decoupling, unused op-amp treatment, and physical connections.
- Next step: specify these interface requirements before creating an editable schematic or building hardware.
