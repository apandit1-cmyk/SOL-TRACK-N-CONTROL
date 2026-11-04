# 01 Building the Circuit - Servo and Turning (90 to 0 Degrees)

For the SunbYte mission to generate enough power, its solar arrays must constantly physically rotate to face the sun. We are going to simulate this mechanical movement using a **Servo Motor**. 

A servo is a special motor that doesn't just spin continuously; it receives a signal telling it exactly what angle to point at (usually between 0 and 180 degrees) and holds that position.

## Building the Circuit

1. **Power the Breadboard:** First, ensure your Arduino's `5V` pin is connected to the breadboard's red `+` rail, and the `GND` pin is connected to the black `-` rail.
2. **Wire the Servo Power:** Your servo has three wires. Connect the **Red** wire to the `+` 5V rail on your breadboard.
3. **Wire the Servo Ground:** Connect the **Brown** (or Black) wire to the `-` GND rail.
4. **Wire the Signal:** Connect the **Orange** (or Yellow/Green) signal wire to Arduino **Digital Pin 2**.

*(Make sure your signal wire is on the same breadboard row as the servo's connector pin!)*
![Activity A Task 2 Circuit](ACTIVITY--TASK-2.png)

## Writing Raw PWM Code

Usually, people use a pre-built "Servo library" to move these motors. But to really understand how spacecraft hardware communicates, we are going to write the raw **Pulse Width Modulation (PWM)** signals ourselves!

Servos expect a pulse of electricity every 20 milliseconds (ms). The *length* of that pulse tells it where to go:
* A pulse of **1500 microseconds** (1.5ms) tells it to go to the middle (90 degrees).
* A pulse of **1000 microseconds** (1.0ms) tells it to go to 0 degrees.

Copy this code into your Arduino IDE and **fill in the blanks (`___`)** to manually generate these pulses:

```cpp
// 01: Raw PWM Servo Control

// Define the pin connected to the servo's signal wire
int servoPin = ___; 

void setup() {
  // Set the servo pin to send power OUT
  pinMode(servoPin, ________);
}

void loop() {
  
  // --- MOVE TO 90 DEGREES ---
  // We repeat this pulse 50 times to give the motor time to physically move there
  for(int i = 0; i < 50; i++) { 
    digitalWrite(servoPin, HIGH); // Start the pulse
    
    // A 1500 microsecond pulse means "Go to 90 degrees"
    delayMicroseconds(____); 
    
    digitalWrite(servoPin, LOW); // End the pulse
    
    // Wait for the rest of the 20 millisecond cycle
    delay(20); 
  }

  // --- MOVE TO 0 DEGREES ---
  for(int i = 0; i < 50; i++) {
    digitalWrite(_______, HIGH);
    
    // A 1000 microsecond pulse means "Go to 0 degrees"
    delayMicroseconds(____);
    
    digitalWrite(servoPin, LOW);
    delay(____); // Wait 20 milliseconds
  }
}
