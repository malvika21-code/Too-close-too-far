# Too-close-too-far
// Basic Level: Ultrasonic Sensor Distance Measurement

// Define pins for the Ultrasonic sensor
const int trigPin = 9;  // Trigger pin
const int echoPin = 10;  // Echo pin

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  
  Serial.begin(9600);  // Start serial communication
}

void loop() {
  long duration, distance;

  // Trigger the ultrasonic sensor pulse
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  // Read echo pulse duration
  duration = pulseIn(echoPin, HIGH);

  // Convert duration to distance in centimeters
  distance = duration * 0.034 / 2;

  // Print distance to the Serial Monitor
  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");

  delay(500);  // Wait before the next reading
}