
[![Arduino CI](https://github.com/RobTillaart/MAX471/workflows/Arduino%20CI/badge.svg)](https://github.com/marketplace/actions/arduino_ci)
[![Arduino-lint](https://github.com/RobTillaart/MAX471/actions/workflows/arduino-lint.yml/badge.svg)](https://github.com/RobTillaart/MAX471/actions/workflows/arduino-lint.yml)
[![JSON check](https://github.com/RobTillaart/MAX471/actions/workflows/jsoncheck.yml/badge.svg)](https://github.com/RobTillaart/MAX471/actions/workflows/jsoncheck.yml)
[![GitHub issues](https://img.shields.io/github/issues/RobTillaart/MAX471.svg)](https://github.com/RobTillaart/MAX471/issues)

[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](https://github.com/RobTillaart/MAX471/blob/master/LICENSE)
[![GitHub release](https://img.shields.io/github/release/RobTillaart/MAX471.svg?maxAge=3600)](https://github.com/RobTillaart/MAX471/releases)
[![PlatformIO Registry](https://badges.registry.platformio.org/packages/robtillaart/library/MAX471.svg)](https://registry.platformio.org/libraries/robtillaart/MAX471)


# MAX471

Arduino library for MAX471 current sensor.


## Description

The MAX471 is a (older) current sensor

a.k.a. GY-471

MAX472 seems to be compatible but has some different wiring.
See datasheet.

The library is experimental and needs more testing.

Feedback, issues and improvements are welcome, 
Please open an issue on GitHub.


#### Limits

**Warning** Use a voltage divider if needed!

|  unit     |  limits    |  notes    |
|:---------:|:----------:|:----------|
|  Power    |  50 Watt   |  total
|  Voltage  |  25 Volt   |  at 2 A
|  Current  |  3 Ampere  |  at 16 V


#### Related

- https://wolles-elektronikkiste.de/en/max471-current-sensor (excellent)


## Connection

- purple board
- red board


## Interface

```cpp
#include "MAX471.h"
```

#### Constructor

- **MAX471(uint8_t currentPin, uint8_t voltagePin)** red + purple board
- **MAX471(uint8_t currentPin, uint8_t voltagePin, uint8_t signPin)** purple board.


#### Configure

- **void begin(float maxVoltage = 5, uint16_t maxSteps = 1023)**
Sets the parameters voltage and maxSteps of the internal ADC.
Note this allows to update the voltage runtime.
Steps must be larger than zero of course, typical 255 (8 bit), 1023 (10 bit), 
4095 (12 bit).

**begin()** can be called multiple times to adjust e.g. the voltage used.
Think of setting the analog reference (AREF) to 1V1.


#### Read

- **float readCurrent(uint8_t times = 1)** returns Ampere
- **float readVoltage(uint8_t times = 1)** returns Volts
- **float calcPower()** returns Watt, but only after current and voltage 
has been read as it uses the cached values.


## Future

#### Must

- improve documentation
- buy hardware MAX471
- test with hardware

#### Should 

- examples
  - plotter
  - integrate current over time.

#### Could

- support shutDown pin. LOW/GND = ON, HIGH = OFF. 
  - not on breakout boards.
- investigate AREF 1V1 to improve resolution.


#### Ideas

- add derivative of current + voltage (raising falling indicator)
- percentage interface
- warning limits reached.

#### Won't


## Support

If you appreciate my libraries, you can support the development and maintenance.
Improve the quality of the libraries by providing issues and Pull Requests, or
donate through PayPal or GitHub sponsors.

Thank you,

