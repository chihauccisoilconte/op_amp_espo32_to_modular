# Project status

Updated: 2026-09-28

- Added README.md describing the intended ESP32 DAC-to-modular-synth audio interface and the amplifier shown in the reference image.
- Renamed Untitled.png to schematic.png and linked it from the README.
- Retained the existing Eurorack_audio_amp_BOM.xlsx without changes.
- Added BOM.md with all eight component rows and the circuit notes from both spreadsheet sheets, plus a clearly separate TL072CP package alternative. Linked it from README.md for GitHub viewing.
- Added a README note on the TL072CP alternative, including DIP-8 versus SO-8 packaging, supply connections, manufacturer links, and a prominent BOM spreadsheet download link. The substitution is documentation-based and has not been hardware-tested.
- Checked the image visually and calculated the ideal gain from the displayed resistor values (−33 kΩ / 10 kΩ = −3.3). Consulted TI and ST documentation for the op-amp substitution. No circuit edits, simulation, ERC/DRC, complete circuit datasheet validation, or hardware tests were performed.
- Open decisions: ESP32 model and DAC range, target audio level, DC-offset handling, power decoupling, unused op-amp treatment, and physical connections.
- Next step: specify these interface requirements before creating an editable schematic or building hardware.
