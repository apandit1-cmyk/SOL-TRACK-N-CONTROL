# 03 Using Serial Monitor & Finishing Up

It is great to see the motor moving, but as engineers, we often need to see the actual math happening behind the scenes to make sure our system is working perfectly. 

We are going to use the **Serial Monitor** to watch our Arduino translate the raw dial readings into the exact microsecond pulses being sent to the servo in real-time.

## Updating the Code for Telemetry

We need to add a few lines to our existing code to open up a communication line with the laptop and print our variables.

Update your code with the new Serial commands, and **fill in the blanks (`___`)**:

```cpp
// 03: Serial Monitor & Finishing Up

int servoPin = 2;
int potPin = A5; 

void setup() {
  pinMode(servoPin, OUTPUT);
  
  // Start the serial connection at 9600 baud
  Serial.begin(____); 
}

void loop() {
  // Read the dial and calculate the pulse
  int potValue = analogRead(potPin);
  int pulseWidth = map(potValue, 0, 1023, 1000, 2000);

  // Send the pulse to the servo
  digitalWrite(servoPin, HIGH);
  delayMicroseconds(pulseWidth); 
  digitalWrite(servoPin, LOW);
  delay(20); 

  // --- PRINT DATA TO THE COMPUTER ---
  Serial.print("Dial Reading: ");
  // Print the raw 0-1023 value
  Serial.print(________); 
  
  Serial.print("  |  Pulse Width (us): ");
  // Print the calculated 1000-2000 value
  Serial.println(________); 
}
