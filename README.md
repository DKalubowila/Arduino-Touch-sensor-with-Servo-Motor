# Arduino-Touch-sensor-with-Servo-Motor
This code helps to control a servo motor using a touch sensor.
You can connect the wires as below.
   1. Connect the touch sensor pin to D2
   2. Connect the servo motor pin to D9
//below is the arduino code
#include <Servo.h>

Servo myServo; // Create a servo object
const int touchPin = 2; // Pin connected to the touch sensor
const int servoPin = 9; // Pin connected to the servo
bool touchState = false; // Variable to store the touch sensor state

void setup() {
  pinMode(touchPin, INPUT);
  myServo.attach(servoPin); // Attach servo to the defined pin
  myServo.write(90); // Start at the neutral position (90 degrees)
}

void loop() {
  touchState = digitalRead(touchPin); // Read the touch sensor state

  if (touchState == HIGH) {
    // If the touch sensor is touched
    myServo.write(45); // Rotate to 45 degrees
    delay(500); // Wait for 0.5 seconds
    myServo.write(135); // Rotate to 135 degrees
    delay(500); // Wait for 0.5 seconds
  } else {
    // If the touch sensor is not touched
    myServo.write(90); // Return to the neutral position
  }
}
