# Ultrasonic-distance

#include <LiquidCrystal.h>
#define echo 6
#define trig 7
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

void setup() {
  pinMode(echo,INPUT);
  pinMode(trig,OUTPUT);
  lcd.begin(16, 2);
  lcd.print("Distance = ");
}

void loop() {
  lcd.setCursor(11,0);
  digitalWrite(trig,LOW);
  digitalWrite(trig,HIGH);
  delayMicroseconds(10);
  digitalWrite(trig,LOW);
  float time = 1.0*pulseIn(echo,HIGH)/1000000.0;
  int distance = 1+340*100.0*time/2.0;
  lcd.print(distance);
  lcd.print(" cm ");
  if(distance >80)
  {digitalWrite(8,HIGH);digitalWrite(9,LOW);
   digitalWrite(10,LOW);}
  else if(distance >40)
  {digitalWrite(8,HIGH);digitalWrite(9,HIGH);
   digitalWrite(10,LOW);}
  else if(distance > 20 )
    {digitalWrite(8,HIGH);digitalWrite(9,HIGH);
   digitalWrite(10,HIGH);}
  
}
 
