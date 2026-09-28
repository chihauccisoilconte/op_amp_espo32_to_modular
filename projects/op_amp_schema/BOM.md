# Eurorack audio amplifier bill of materials

This table transcribes the **Bill of Materials** sheet in [Eurorack_audio_amp_BOM.xlsx](Eurorack_audio_amp_BOM.xlsx) so it can be read and reviewed on GitHub. Quantities are for one amplifier circuit as shown in [schematic.png](schematic.png). Package choices are suggestions from the workbook, not verified PCB footprints. No manufacturer part numbers, distributor parts, prices, or stock are specified.

| Reference | Category | Value / part | Qty | Function | Suggested type | Package / footprint | Critical rating | Notes |
| --- | --- | --- | ---: | --- | --- | --- | --- | --- |
| U8 | Op-amp | TL072CDT | 1 | Main inverting audio amplifier | Dual JFET-input audio op-amp | SO-8 / verify against PCB | Must tolerate ±12 V rails | Only U8.1 is used in the shown signal path; terminate the unused half correctly. |
| R5 | Resistor | 10 kΩ | 1 | Input resistor; sets gain together with R25 | Metal film, 1% | 0805 / 0603 / THT as preferred | ≥ 0.1 W | With R25 = 33 kΩ, nominal voltage gain is −3.3 V/V. |
| R25 | Resistor | 33 kΩ | 1 | Op-amp feedback resistor | Metal film, 1% | 0805 / 0603 / THT as preferred | ≥ 0.1 W | In parallel with C19. |
| R23 | Resistor | 1 kΩ | 1 | Series output isolation / protection | Metal film, 1% | 0805 / 0603 / THT as preferred | ≥ 0.1 W | Between TL072 output and J2 tip. |
| C3 | Capacitor | 1 nF | 1 | Input high-frequency shunt filter | C0G / NP0 ceramic preferred | 0805 / 0603 / THT as preferred | ≥ 25 V | Connected from the J1 input signal node to AGND. |
| C19 | Capacitor | 100 pF | 1 | Feedback compensation capacitor | C0G / NP0 ceramic preferred | 0805 / 0603 / THT as preferred | ≥ 25 V | In parallel with R25; feedback pole is approximately 48 kHz. |
| J1 | Audio jack | 3.5 mm mono mini-jack | 1 | Analog audio input from DAC / external source | Eurorack-compatible TS jack | Panel-mount or PCB-mount to suit enclosure | Audio signal level | Tip = AUDIO IN; sleeve = AGND. A switched jack is optional, not required. |
| J2 | Audio jack | 3.5 mm mono mini-jack | 1 | Amplified audio output | Eurorack-compatible TS jack | Panel-mount or PCB-mount to suit enclosure | Audio signal level | Tip = AUDIO OUT; sleeve = AGND. |

## Package alternative

TL072CP is a through-hole DIP-8 option for U8 with the same pin numbering. It requires a DIP-8 footprint or socket; it cannot be placed on the SO-8 pads specified for TL072CDT. This alternative is documented in the [README](README.md#tl072cp-alternative-and-bill-of-materials) and is **not** an additional BOM quantity.

## Circuit notes from the workbook

| Item | Specification / note |
| --- | --- |
| Input connector | J1: 3.5 mm TS mini-jack. Tip carries DAC/external audio; sleeve connects to AGND. |
| Output connector | J2: 3.5 mm TS mini-jack. Tip is driven through R23; sleeve connects to AGND. |
| Topology | Inverting TL072 amplifier stage. |
| Nominal gain | −R25/R5 = −33 kΩ / 10 kΩ = −3.3 V/V. |
| Supply | TL072 powered from +12 V and −12 V. |
| Feedback network | R25 = 33 kΩ in parallel with C19 = 100 pF. |
| Approx. feedback pole | About 48 kHz. |
| Grounding | Use AGND for both jack sleeves and the analog signal ground. |
| Eurorack note | The shown circuit handles the audio path only. A complete Eurorack module normally also needs a proper ±12 V power connector and local supply decoupling. |
| Recommended decoupling | Add 100 nF ceramic close to the TL072 supply pins: +12 V to AGND and −12 V to AGND. Bulk decoupling such as 10 µF per rail is also commonly used. |
| Unused TL072 section | Do not leave the second op-amp inputs floating; configure the unused section in a stable state. |
| DAC caution | If the DAC jack is a headphone-level output rather than line-level, check maximum amplitude because the −3.3 V/V stage can clip at high input levels. |

The suggested decoupling parts and power connector are **not included** in the eight BOM rows because they are absent from the shown circuit. See [STATUS.md](STATUS.md) for unresolved design decisions.
