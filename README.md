# Practica-sensor-nivel-de-agua
Se utilizarán leds como guía visual del sensor ultrasónico y se mostrará en la display

## Introduccion

### Descripcion 

La display nos mostrará de acuerdo a la guía de los leds el nivel del tanque 

### Material necesario

- WOKWI
- Tarjeta ESP32
- Sensor ultrasonico
- LCD 16x2 (I2C)
- 4 led
- 4 resistencias de 220 homs
- Símbolo GND

## Instrucciones

### Requisitos previos 

Para poder usar este repositorio deberás entrar a la plataforma WOKWI

https://wokwi.com/

### Instrucciones de prepracion de entorno

1. Abrir la terminal de programación y colocar las siguientes líneas

```
// defines pins numbers
const int trigPin = 4;
const int echoPin = 15;
const int led1 = 16;
const int led2 = 0;
const int led3 = 2;
const int led4 = 18;

// defines variables
long duration;
int distance;
int safetyDistance;
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4
LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {
pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
pinMode(echoPin, INPUT); // Sets the echoPin as an Input
pinMode(led1, OUTPUT);
pinMode(led2, OUTPUT);
pinMode(led3, OUTPUT);
pinMode(led4, OUTPUT);
Serial.begin(9600); // Starts the serial communication
 lcd.init();
 lcd.backlight();
}


void loop() {
// Clears the trigPin
digitalWrite(trigPin, LOW);
delayMicroseconds(2);

// Sets the trigPin on HIGH state for 10 micro seconds
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);

// Reads the echoPin, returns the sound wave travel time in microseconds
duration = pulseIn(echoPin, HIGH);

// Calculating the distance
distance= duration*0.034/2;

safetyDistance = distance;
if (safetyDistance>=10 && safetyDistance<=98)
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
   lcd.setCursor(0, 0);
  lcd.print("Diplomado");
  lcd.setCursor(0, 1);
  lcd.print("Automatizacion");
  delay (2000);
  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("Irving Cardoso");
  lcd.setCursor(0, 1);
  lcd.print("Ing Mecanica");
  delay (2000);
  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("  07/06/2025");
  delay (2000);
  lcd.clear();
  lcd.setCursor(0,0);
  lcd.print("Distancia: "+ String (distance)+"cm");
  lcd.setCursor(0,1);
  lcd.print("Nivel 1/4");
  delay(2000);          
  lcd.clear();
}
else if(safetyDistance>=99 && safetyDistance<=198) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
     lcd.setCursor(0, 0);
  lcd.print("Diplomado");
  lcd.setCursor(0, 1);
  lcd.print("Automatizacion");
  delay (2000);
  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("Irving Cardoso");
  lcd.setCursor(0, 1);
  lcd.print("Ing Mecanica");
  delay (2000);
  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("  07/06/2025");
  delay (2000);
  lcd.clear();
  lcd.setCursor(0,0);
  lcd.print("Distancia: "+ String (distance)+"cm");
  lcd.setCursor(0,1);
  lcd.print("Nivel 1/2");
  delay(2000);          
  lcd.clear();
}
else if (safetyDistance>=199 && safetyDistance<=298) 
{
 digitalWrite(led1,  HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, LOW);
     lcd.setCursor(0, 0);
  lcd.print("Diplomado");
  lcd.setCursor(0, 1);
  lcd.print("Automatizacion");
  delay (2000);
  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("Irving Cardoso");
  lcd.setCursor(0, 1);
  lcd.print("Ing Mecanica");
  delay (2000);
  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("  07/06/2025");
  delay (2000);
  lcd.clear();
  lcd.setCursor(0,0);
  lcd.print("Distancia: "+ String (distance)+"cm");
  lcd.setCursor(0,1);
  lcd.print("Nivel 3/4");
  delay(2000);          
  lcd.clear();
}
else if (safetyDistance>=299 && safetyDistance<=398) 
{
 digitalWrite(led1,  HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, HIGH);
     lcd.setCursor(0, 0);
  lcd.print("Diplomado");
  lcd.setCursor(0, 1);
  lcd.print("Automatizacion");
  delay (2000);
  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("Irving Cardoso");
  lcd.setCursor(0, 1);
  lcd.print("Ing Mecanica");
  delay (2000);
  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("  07/06/2025");
  delay (2000);
  lcd.clear();
  lcd.setCursor(0,0);
  lcd.print("Distancia: "+ String (distance)+"cm");
  lcd.setCursor(0,1);
  lcd.print("Nivel lleno");
  delay(2000);          
  lcd.clear();
}
// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);
delay (2000);
}
```
2.Instalar la librería LiquidCrystal I2C como se muestra en la siguiente imagen

![image](https://github.com/user-attachments/assets/cd10587a-3148-4899-b414-56133ed7e439)


3.Hacer la conexión como se muestra en la siguiente imagen


