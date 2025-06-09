# Spring103Final "Chase"
Final for ENGR. 103H  
My game "Chase" consists of an LED traveling around the LED's in a small circle, or "chasing."
Once the game starts, the player presses the button to make the moving LED pause on the LED number of choice (and it emits a small tone).
The goal of the game is to "stop" on each of the LEDs in a sequence. 
Ordinary sequence can be a simple "1, 2, 3, 4, etc." but can also be altered by player to increase to desired difficulty. 
Most accurate completion of the sequence wins.  

// Define the LED pins  
const int ledPins[] = {1, 2, 3, 4, 5, 6, 7, 8, 9}; // My pins  
const int numLeds = sizeof(ledPins) / sizeof(ledPins[0]); // The number of LEDs  
const int switchPin = 7; // Switch is enabled  
const int buttonPin = 4; // Define the pin  
const int speakerPin = 8; // The speaker pin  
const int noteFrequency = 440; // 440 Hz  
bool chasing = true; // LED "chasing"  
int currentLed = 0; // Current LED in the sequence

void setup() {  
pinMode(switchPin, INPUT); // Set the switch pin as an input  
pinMode(buttonPin, INPUT_PULLUP);   // Set the button pin as an input  
pinMode(speakerPin, OUTPUT); // Set the speaker pin as an output  
for (int i = 0; i < numLeds; i++) {  // Set all LED pins as outputs  
pinMode(ledPins[i], OUTPUT);  
}}

void loop() { // Check state  
int switchState = digitalRead(switchPin);  
int buttonState = digitalRead(buttonPin);  
if (switchState == HIGH) {  
digitalWrite(ledPins,LOW);  
} else {  
if (buttonState == LOW && chasing) { // Button is pressed  
chasing = false;  
tone(speakerPin, noteFrequency);  
} else {  
noTone(speakerPin);  
if (chasing) {  
digitalWrite(ledPins[currentLed], LOW); // Turn off the previous LED  
currentLed = (currentLed + 1) % numLeds; // Advance to the next LED  
digitalWrite(ledPins[currentLed], HIGH); // Turn on the current LED  
delay(300); //Add a delay for the effect (adjust as needed)  
}}}}
