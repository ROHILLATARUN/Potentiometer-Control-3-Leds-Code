# Potentiometer-Control-3-Leds-Code
// Define pins for LEDs
const int led1 = 13;
const int led2 = 2;
const int led3 = 3;
const int potPin = A0;  // Potentiometer connected to A0

int potValue = 0;       // Variable to store potentiometer value
int ledPattern = 0;     // Variable to store current LED pattern

void setup() {
  pinMode(led1, OUTPUT);
  pinMode(led2, OUTPUT);
  pinMode(led3, OUTPUT);
  Serial.begin(9600);   // Initialize serial communication
}

void loop() {
  // Read the potentiometer value (0 - 1023)
  potValue = analogRead(potPin);

  // Map the potentiometer value to 10 patterns (0 - 9)
  ledPattern = map(potValue, 0, 1023, 0, 9);
  
  // Print potentiometer value and pattern for debugging
  Serial.print("Potentiometer Value: ");
  Serial.print(potValue);
  Serial.print(" | LED Pattern: ");
  Serial.println(ledPattern);
  
  // Choose the pattern based on potentiometer position
  switch (ledPattern) {
    case 0:
      pattern0();
      break;
    case 1:
      pattern1();
      break;
    case 2:
      pattern2();
      break;
    case 3:
      pattern3();
      break;
    case 4:
      pattern4();
      break;
    case 5:
      pattern5();
      break;
    case 6:
      pattern6();
      break;
    case 7:
      pattern7();
      break;
    case 8:
      pattern8();
      break;
    case 9:
      pattern9();
      break;
  }
}

// Pattern 0: LEDs all ON
void pattern0() {
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
}

// Pattern 1: LEDs all OFF
void pattern1() {
  digitalWrite(led1, LOW);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
}

// Pattern 2: LED1 blinking
void pattern2() {
  digitalWrite(led1, HIGH);
  delay(300);
  digitalWrite(led1, LOW);
  delay(300);
}

// Pattern 3: LED2 blinking
void pattern3() {
  digitalWrite(led2, HIGH);
  delay(300);
  digitalWrite(led2, LOW);
  delay(300);
}

// Pattern 4: LED3 blinking
void pattern4() {
  digitalWrite(led3, HIGH);
  delay(300);
  digitalWrite(led3, LOW);
  delay(300);
}

// Pattern 5: LEDs alternate (LED1 & LED2)
void pattern5() {
  digitalWrite(led1, HIGH);
  digitalWrite(led2, LOW);
  delay(300);
  digitalWrite(led1, LOW);
  digitalWrite(led2, HIGH);
  delay(300);
}

// Pattern 6: LEDs alternate (LED1 & LED3)
void pattern6() {
  digitalWrite(led1, HIGH);
  digitalWrite(led3, LOW);
  delay(300);
  digitalWrite(led1, LOW);
  digitalWrite(led3, HIGH);
  delay(300);
}

// Pattern 7: All LEDs blink together
void pattern7() {
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  delay(500);
  digitalWrite(led1, LOW);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  delay(500);
}

// Pattern 8: Sequential blinking (LED1 -> LED2 -> LED3)
void pattern8() {
  digitalWrite(led1, HIGH);
  delay(300);
  digitalWrite(led1, LOW);
  digitalWrite(led2, HIGH);
  delay(300);
  digitalWrite(led2, LOW);
  digitalWrite(led3, HIGH);
  delay(300);
  digitalWrite(led3, LOW);
}

// Pattern 9: Fast alternating (LED1 -> LED2 -> LED3, fast)
void pattern9() {
  digitalWrite(led1, HIGH);
  delay(100);
  digitalWrite(led1, LOW);
  digitalWrite(led2, HIGH);
  delay(100);
  digitalWrite(led2, LOW);
  digitalWrite(led3, HIGH);
  delay(100);
  digitalWrite(led3, LOW);
}
