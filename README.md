# Practica-ESP32-con DHT11 y Lcd
Este repositorio muestra cómo programar un ESP32 usando el sensor DHT11 y muestra los datos obtenidos mostrados en una pantalla LCD.

## Introducción   
Descripción 
ESP32 se utiliza en un ambiente de adquisición de datos, por lo que en esta práctica usaremos un sensor DHT11 para obtener registros de temperatura y humedad del ambiente. Estos registros se mostrarán visualmente en la pantalla LCD. Para este ejercicio se utiliza un simulador llamado WOKWI.

Para realizar esta práctica necesitas lo siguiente:

WOKWI Tarjeta ESP32 Sensor DHT11 LCD 16x2 (I2C
    
Entrar a la plataforma WOKWI para poder usar el sensor Posterior colacamos abrimos el programa y colocamos el codigo de programación:
## Codigo 
#include "DHTesp.h" 
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR 0x27 
#define LCD_COLUMNS 20 
#define LCD_LINES 4

const int DHT_PIN = 15;

DHTesp dhtSensor;

LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {

Serial.begin(115200); 
dhtSensor.setup(DHT_PIN, DHTesp::DHT22); 
lcd.init(); 
lcd.backlight();
}
void loop() {
TempAndHumidity data = dhtSensor.getTempAndHumidity(); 
Serial.println("Temp: " + String(data.temperature, 1) + "°C");
Serial.println("Humidity: " + String(data.humidity, 1) + "%");
Serial.println("---");
lcd.setCursor(0, 0); 
lcd.print(" Temp: " + String(data.temperature, 1) + "\xDF"+"C ");
lcd.setCursor(0, 1); lcd.print(" Humidity: " + String(data.humidity, 1) + "% "); 
lcd.print("Wokwi Online IoT");
delay(1000); }

- 2.Instalar la libreria de DHT sensor library for ESPx  y la libreria Liquid Crystal I2C como se muestra en la siguente imagen.
![](https://github.com/AmaiCisneros/Practica3/blob/main/1.png)

- 3.Realizamos la conexion de los sensores DHT11 y  ESP32 con el sensor LDC 16X2 (12C) y agregamos VCC Symbol y GND Symbol como se muestra en la siguente imagen.
![]( )

-4. Iniciamos el simulador.
    -Se proyectan los datos en el monitor serial.
    -Se observan los resultados en la pantalla LCD.
    
Se muestra en la siguente imagen.
![]( )
  
