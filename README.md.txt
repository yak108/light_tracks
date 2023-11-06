# Arduino Nano with Dual TLC5940 LED Drivers

This project uses an Arduino Nano to control a series of LEDs using two daisy-chained TLC5940 LED drivers. The Arduino Nano orchestrates the lighting effects to simulate a car moving around a race track.

## Connections

### Arduino Nano to TLC5940 (TLC1)

- **5V** (Arduino) to **VCC** (TLC1)
- **GND** (Arduino) to **GND** (TLC1)
- **D11** (MOSI, Arduino) to **SIN** (Serial IN, TLC1)
- **D13** (SCLK, Arduino) to **SCLK** (Serial Clock, TLC1)
- **D9** (Arduino) to **XLAT** (Latch, TLC1)
- **D10** (Arduino) to **BLANK** (Blank, TLC1)
- **D3** (PWM, Arduino) to **GSCLK** (Grayscale Clock, TLC1)

### TLC5940 (TLC1) to TLC5940 (TLC2)

- **SOUT** (Serial OUT, TLC1) to **SIN** (Serial IN, TLC2)
- **VCC** and **GND** pins connected in parallel between TLC1 and TLC2
- **SCLK**, **XLAT**, **BLANK**, and **GSCLK** connected in parallel from TLC1 to the corresponding pins on TLC2

### Common Connections

- Both **IREF** pins (TLC1 and TLC2) connected together and to a resistor that sets the current for the LEDs (value calculated based on LED specifications).

## Pin Descriptions

- **VCC**: Power supply for the TLC5940, usually connected to 5V.
- **GND**: Ground connection.
- **SIN (Serial IN)**: Serial data input, receives grayscale data from the Arduino.
- **SOUT (Serial OUT)**: Serial data output, sends data to the next TLC5940 in the chain.
- **SCLK (Serial Clock)**: Clock signal for serial communication, synchronizes data transmission.
- **XLAT (Latch)**: Latches the data into the TLC5940's internal registers.
- **BLANK**: When pulled high, turns off all outputs; when low, allows outputs to be controlled by grayscale data.
- **GSCLK (Grayscale Clock)**: Provides the clock signal for grayscale PWM control of the LEDs.

## Usage

The LEDs are connected to the output pins of the TLC5940s. To create the illusion of a car moving on a race track, the Arduino sequentially turns on and off the LEDs by sending updated grayscale data to the TLC5940 chips.

A single resistor connected to the IREF pin sets the current for all the LEDs connected to both TLC5940s, ensuring uniform brightness.

The Arduino sketch controls the timing and sequence of LED illumination to simulate movement along the track.

## Additional Notes

- Ensure that the power supply can handle the total current draw when all LEDs are on.
- Use appropriate resistors to limit the LED current as required by their specifications.
- Software libraries for the TLC5940 can simplify the coding process and are recommended for managing daisy-chained configurations.

