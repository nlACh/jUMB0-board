# The jUMB0 Board!

This is a 3D printer control board based on the STM32F407VET6 MCU. It is a cortex M4F core, implementing a floating point unit.
[Marlin Firmware](marlinfirmware.org) is already ported to STM32 MCUs. So this board will work as usual.
FInd Marlin source code at [https://github.com/marlinfirmware/Marlin.git](https://github.com/marlinfirmware/Marlin.git)

The following features are expected to be implemented in this board:

| Connections | Number of Ports/Pins exposed | Usage |
| ----------- | ---------------------------- | ----- |
| SPI | 2\* | <ul><li>SPI2 pins for the stepper motor drivers (TMC2130, TMC5160, etc)</li><li>SPI1 pins for GLCD+SD card, or with something else</li></ul> |
| I2C | 1 | Port for whatever use comes up |
| PWM | 10 | <ul><li>6 PWM pins for heaters (enclosure heater is optional)</li><li>4 PWM pins for servo motors</li></ul> |
| UART | 3 (for now) | <ul><li>USART\_ reserved for FTDI programming or other peripherals</li><li>2 U(S)ARTx motor drivers (TMC2208, TMC2209, etc)</li></ul> |
| USB | 1 | Full usb support, for DFU mode, and virtual COM support as well |
| ADC | 6 | Heater thermistor pins<br><ul><li>4 for toolhead</li><li>1 for bed</li><li>1 for enclosure (optional)</li></ul> |
| GPIO | 6 | Limit switch action |
| GPIO | 3x | 3 GPIO pins per stepper driver<br><ul><li>1 ENABLE pin</li><li>2^ for STEP/DIR control (for traditional control DRV8825, A4988, etc)</li></ul> |

\* For SPI2 extra CS pins required per driver.
^ These pins may be repurposed for SPI2 and U(S)ART lines depending on functional overlap.

Total pins exposed for MCU = 100 (including VCC, VSS, BOOTx and HSE, LSE pins).