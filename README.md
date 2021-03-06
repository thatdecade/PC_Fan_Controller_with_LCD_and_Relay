# PC Fan Controller with LCD
Arduino to control a 12V PC fan and displays status on LCD. Bargraph and tachometer RPM speed. Basic operation is below.

 - Supports any 4-bit or 8-bit LCD.  Default is 16x2 characters
 - Button inputs are software debounced
 - Main loop uses a scheduler 
 - See code for list of configurable values

# onoff_state = SYSTEM_OFF
Pressing on/off will:
* Command mosfet/relay to power to the fan
* Set the throttle to 20% (first boot) or last selected

# onoff_state = SYSTEM_ON
Pressing on/off will:
* Command mosfet/relay to remove power from the fan
* Set the throttle to OFF
Use the +/- buttons to go up and down in 10% chunks
HOLDING (3 second count) on/off will set throttle to MAX_FAN_SPEED

When max speed is reached:
* Do not increase the pwm farther.
* A message is displayed to hold button to access fan speed beyond pwm = 255

When on/off is held for 3 seconds:
* Turn off PWM and ground the pin.
* This will set the fan to it's true max speed.

# Current Bugs
- PWM library sets the Fan control PWM to 3.9khz instead of 25khz.  Seems to work ok still.
