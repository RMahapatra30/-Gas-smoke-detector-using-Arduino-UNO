# -Gas-smoke-detector-using-Arduino-UNO
Codes for MQ-2 Gas/ Smoke Sensor with Arduino:

int ledPinRed = 12;       // Pin number for the red LED
int ledPinGreen = 11;     // Pin number for the green LED
int buzzerPin = 10;       // Pin number for the buzzer
int smokeSensorPin = A5;  // Analog input pin for the smoke sensor
int sensorThreshold = 400; // Threshold value for smoke detection

void setup() {
  pinMode(ledPinRed, OUTPUT);
  pinMode(ledPinGreen, OUTPUT);
  pinMode(buzzerPin, OUTPUT);
  pinMode(smokeSensorPin, INPUT);
  Serial.begin(9600);
}

void loop() {
  int analogSensor = analogRead(smokeSensorPin);

  Serial.print("Smoke Sensor Reading: ");
  Serial.println(analogSensor);
  
  // Checks if the smoke sensor reading has reached the threshold value
  if (analogSensor > sensorThreshold)
  {
    digitalWrite(ledPinRed, HIGH);
    digitalWrite(ledPinGreen, LOW);
    tone(buzzerPin, 1000, 200);
  }
  else
  {
