# Automatic Sandwich Making Machine

A first-year university hardware project exploring Arduino programming, sensor input, actuator control, and a keypad/LCD interface for a sandwich-making prototype.

## Project materials

- [Arduino sketch](code/Automatic_Sandwich_Making_Machine.ino)
- [Circuit schematic](images/Circuit_Schematic.png)
- [PCB design](images/PCB_design.png) and [3D PCB view](images/PCB_3D.png)
- [Circuit board photo](images/circuit%20board.jpg)
- [Assembly animation](animation/Automatic_Sandwich_Maker_Animation_Video.avi)

## Explore and reproduce

```bash
git clone https://github.com/paranietharan/Automatic-Sandwich-Making-Machine.git
cd Automatic-Sandwich-Making-Machine
```

Open the sketch in the Arduino IDE. If prompted, place it in a sketch folder named `Automatic_Sandwich_Making_Machine`. Install the libraries required by its includes: `LiquidCrystal_I2C`, `Keypad`, and `Servo`; `Wire` is supplied by the Arduino core.

Select a board compatible with the pin assignments in the sketch and match the wiring to the schematic. The code uses pins through 53, a 16×2 LCD at I2C address `0x27`, a 4×4 keypad, ultrasonic sensors, an IR sensor, a servo, stepper-control outputs, and a relay. Board and library versions are not pinned in this repository, so check the configuration against the physical prototype before uploading.

## Learning context

This repository preserves the source and design artifacts from the university prototype. Its value is the integration of software with a physical mechanism; it is not a specification for a production appliance.

## Sketch walkthrough
Arduino sketch for a sandwich-making machine that uses various components such as a servo motor, ultrasonic sensors, a keypad, and more. 
This code is designed for a sandwich-making machine that allows the user to select toppings, adds toppings, and assembles a sandwich, displaying messages on an LCD screen throughout the process. It also includes sensor checks to ensure that the required ingredients are available before making the sandwich.

### Code organization

Include Libraries: The code includes several libraries for different components, such as Wire (for I2C communication), LiquidCrystal_I2C (for the LCD display), Keypad (for keypad input), and Servo (for controlling the servo motor).

Define Constants: Several constants are defined to specify pin numbers for various components, such as the relay pin, IR sensor pin, and pins for ultrasonic sensors. The code also sets up some pins for controlling stepper motors.

Servo Motor: A servo motor is initialized and attached to a specific pin. The pos variable is used to control the servo's position.

Keypad: The code sets up the configuration for a 4x4 keypad, including the layout of keys and pin connections.

Toppings: An array of available toppings is defined, and a variable to keep track of selected toppings is initialized.

Stepper Motors: The code sets up pins for controlling stepper motors, defines the steps per revolution and step sequence, and initializes variables to track the current step and the step delay.

Setup Function: The setup function initializes various components, sets pin modes, and prepares the system for operation.

Loop Function: The main part of the code is in the loop function, which executes various tasks:

Checking the status of chambers (bread, carrot, leaks, and eggs).
Displaying messages on an LCD to indicate the status of the machine.
Allowing the user to select toppings using a keypad.
Controlling stepper motors to dispense selected toppings.
Adding bread slices using a servo motor.
Applying sauce using a relay to control a solenoid valve.
Detecting the presence of a sandwich using an IR sensor.
Displaying messages on the LCD to inform the user about the progress and completion of the sandwich-making process.
Ultrasonic Sensor Functions: There are separate functions to check the status of bread, carrot, leaks, and eggs using ultrasonic sensors. These functions use the pulseIn function to measure distances based on the sensor's response.

Stepper Motor Functions: There are functions to rotate the stepper motors for adding various toppings such as carrots, leaks, and scrambled eggs.

Servo Motor Function: The AddBreadSlice function controls the servo motor to add bread slices.

Relay (Solenoid Valve) Function: The putSauce function turns on a relay to apply sauce.

IR Sensor Function: The detectSandwich function checks the presence of a sandwich using an IR sensor.
