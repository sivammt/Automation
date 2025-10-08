# Automation
Sensing-Control-Actuation
// Automatic Plant Watering System

const int moistureSensorPin = A0; // Analog pin for soil moisture sensor
const int pumpRelayPin = 8;       // Digital pin for relay module controlling pump
const int moistureThreshold = 400; // Adjust this value based on your sensor

void setup() {
  pinMode(pumpRelayPin, OUTPUT);
  digitalWrite(pumpRelayPin, LOW); // Pump off initially
  Serial.begin(9600);
}

void loop() {
  int moistureLevel = analogRead(moistureSensorPin);
  Serial.print("Soil Moisture: ");
  Serial.println(moistureLevel);

  if (moistureLevel < moistureThreshold) {
    // Soil is dry, turn on pump
    digitalWrite(pumpRelayPin, HIGH);
    Serial.println("Pump ON");
  } else {
    // Soil is wet, turn off pump
    digitalWrite(pumpRelayPin, LOW);
    Serial.println("Pump OFF");
  }
  delay(5000); // Check every 5 seconds
}
