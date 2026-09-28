# ESP32 DAC to modular synth audio interface

This project is an analog amplifier stage intended to connect the audio output of an ESP32 DAC to a modular synthesizer. Its purpose is to amplify the DAC signal for use in a Eurorack audio signal path.

![Schematic of the audio amplifier stage](schematic.png)

## How it works

The schematic shows one half of a TL072CDT op-amp powered from +12 V and −12 V, with its non-inverting input connected to analog ground (AGND). The DAC signal enters at AUDIO IN and passes through R5 (10 kΩ) to the inverting input. R25 (33 kΩ) provides feedback, giving an ideal low-frequency gain of:

`Vout = −(33 kΩ / 10 kΩ) × Vin = −3.3 × Vin`

The stage therefore amplifies the signal and reverses its polarity. C19 (100 pF), across the feedback resistor, reduces gain at high frequencies. C3 (1 nF) connects the input to ground to shunt high-frequency content; its effect depends on the source impedance. R23 (1 kΩ) is in series with AUDIO OUT, so the connected load also affects the delivered output level.

The intended signal path is **ESP32 DAC → AUDIO IN → amplifier → AUDIO OUT → modular synth audio input**, with a shared signal ground.

## Integration status

This drawing is a starting point for the interface, not a tested complete ESP32 module. In particular, it does not show AC coupling or a circuit to remove the DAC's DC offset. Any DC voltage at the input is also amplified and inverted, which must be accounted for when setting the output level and available headroom. The ESP32 model, DAC output range, and desired modular audio level still need to be specified.

Power-supply decoupling, treatment of the unused op-amp channel, connector details, and the complete ESP32 connection also need to be documented before building the finished interface. This project currently contains no editable KiCad schematic or PCB layout, and no simulation or hardware test results are recorded.

## Files

- [schematic.png](schematic.png): reference drawing of the amplifier stage.
- [Eurorack_audio_amp_BOM.xlsx](Eurorack_audio_amp_BOM.xlsx): existing bill of materials spreadsheet.
- [STATUS.md](STATUS.md): project status and remaining work.

The circuit description above is based on the supplied schematic image; component pinouts and operating limits have not been checked against manufacturer datasheets in this documentation update.
