# SwitchBot Relay Switch 1

This is a beautifully small ESPHome compatible relay module at a good price.  It's 4.2 x 3.7 x 1.6 cm (1.8 x 1.5 x 0.62 inches).  It can fit inside a typical electrical box with a switch or wiring connections already installed.  The internal chip is an ESP32-C3, and the board has exposed test points for easy access to re-flash the ESP with ESPHome.

The module is best mounted in a plastic electrical box with a plastic face plate.  If the module is put in a grounded metal box with a metal face plate, wireless performance will be dramatically affected.

The terminal block can accept up to 14 AWG wires.  If you use stranded wire, it's strongly recommended you use a ferrule before inserting the wire into the terminal block.

## Communication and Control
It supports 2.4G WiFi and Bluetooth 4.2.  The switch can be controlled wirelessly, and can be controlled with a manual switch connected to the terminal block.
??? Can the relay be toggled if the switch is closed ???

## Accessible components
- Electromechanical relay tied to GPIOxxx.  It closes the load circuit when the pin is HIGH/LOW and opens when the pin is HIGH?LOW
- White LED tied to GPIOxx.  LED is on when the pin is HIGH/LOW.  
- Blue LED tied to GPIOxx.  LED is on when the pin is HIGH/LOW
- Switch input tied to GPIOxx.
- Pushbutton on the bottom of the module
- Bluetooth is available

The LEDs are on the bottom of the module, and are quite small, so aren't useful for general and daily user feedback.

The pushbutton is also on the bottom of the module and protected from being easily pressed.
  
## Switched power capabilities
- 100-240 VAC 50/60 Hz up to 16 Amps or 
- 24-48 VDC up to 10 Amps

## Module power source:
- 100-240 VAC 50/60 Hz
- 12 VDC
- 24-48 VDC

## Shucking
The case isn't glued or welded, so it's easy to open up.  You'll probably have to remove the Matter sticker on the back.  There is one tab on each side, right next to the terminal block, and one in the middle on the opposite side.  Slightly pry the edge of the top of the case to release the tabs.  Once all three tabs are released, the bottom cover comes off.  The top of the case is lightly glued to the relay, but it doesn't have to be pulled off to re-flash the ESP since the test points are on the bottom of the circuit board.

## Pin Definitions
White LED (output) - GPIOxx, Active HIGH?LOW
Blue LED (output) - GPIOxx, Active HIGH?LOW
Relay (output) - GPIOxx, Active HIGH?LOW
User Switch (input) -  GPIOxx, Active HIGH?LOW
Pushbutton (input) -  GPIOxx, Active HIGH?LOW

## Baseline ESPHome Configuration
The attached YAML file preps the module for OTA updates.  It can be manipulated by the user to provide customized 

## Flash Procedure
Connect a USB-to-UART adapter to the board.  Attach Rx on the adapter to TX on the module. Attach Tx on the adapter to RX on the module. Attach a wire between P09 on the board to a pushbutton.  Connect the other terminal of the pushbutton to ground.  Attach 3.3v from the adapter to a switch and the other switch terminal to the 3v3 test point on the module.

Ensure the switch is turned off and connect the UART adapter to your computer.

Compile the ESPHome code.

Navigate to the folder containing the firmware and open it in terminal.

esptool.py --no-stub write_flash 0x10000 firmware.bin
