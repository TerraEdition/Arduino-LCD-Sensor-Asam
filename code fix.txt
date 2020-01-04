#include <LiquidCrystal.h>
#define analogInPin A0  //sambungkan kabel hitam (output) ke pin A0
int sensorValue = 0;        //ADC value from sensor
float outputValue = 0.0;        //pH value after conversion

const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 3, d7 = 2;

LiquidCrystal lcd(rs, en, d4, d5, d6, d7);

void setup() {
  // set up the LCD's number of columns and rows:
  Serial.begin(9600);
  lcd.begin(16, 2);
}

void loop() {
sensorValue = analogRead(analogInPin);
outputValue = (-0.0693*sensorValue)+7.3855;
  // set the cursor to (0,0):
  lcd.setCursor(0, 0);
    lcd.print("Sensor ADC= ");
    lcd.print(sensorValue);
  lcd.setCursor(0, 1);
    lcd.print("Output Ph= ");
    lcd.print(outputValue);
    delay(1000);
  lcd.clear();
}