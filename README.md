# PRACTICA-N3 ESP32 SENSOR DHT22 CON LCD
Este repositorio muestra como podemos programar una ESP32 con el sensor DHT22 y mostrando el resutado en la LCD.

## Introducción

### Descripción

La ```Esp32``` la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (```DTH22```) para obtener temperatura y humedad, ademas agrgaremos un (```LCD 16X2 I2C```) para mostrar los resultados en la pantalla lcd; Esta practica se usara un simulador llamado [WOKWI](https://wokwi.com/).


## Material Necesario

A continuacion se utilizaron los siguientes materiales.

- [WOKWI](https://https://wokwi.com/)
- Tarjeta ESP 32
- Sensor DHT22
- LCD 16X2 I2C


## Instrucciones

### Requisitos previos

Para realizar la practica de este repositorio se necesita entrar a la plataforma [WOKWI](https://https://wokwi.com/).


### Instrucciones de preparación de entorno 

1. Abrir la terminal de programación y colocar la siguente codigo:

```
#include "DHTesp.h"
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4

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

  TempAndHumidity  data = dhtSensor.getTempAndHumidity();
  Serial.println("Temp: " + String(data.temperature, 1) + "°C");
  Serial.println("Humidity: " + String(data.humidity, 1) + "%");
  Serial.println("---");
  
  lcd.setCursor(0, 0);
  lcd.print("  Temp: " + String(data.temperature, 1) + "\xDF"+"C  ");
  lcd.setCursor(0, 1);
  lcd.print(" Humidity: " + String(data.humidity, 1) + "% ");
  lcd.print("Wokwi Online IoT");

  delay(1000);
}
```


2. Instalar la libreria de **DHT sensor library for ESPx**. 
   - Seleccionar pestaña de Librery Manager --> Add a New library --> Colocamos el nombre de libreria 

![](https://github.com/DanielX834/PRACTICA-N3/assets/154008369/eeb00235-c4b1-4026-846e-a70497d3224a)


3. Instalar la libreria de **Cristal líquido I2C**. 
   - Seleccionar pestaña de Librery Manager --> Add a New library --> Colocamos el nombre de libreria
   
![](https://github.com/DanielX834/PRACTICA-N3/blob/main/2LibreriaL2C.jpg?raw=true)

 4. Hacer la conexion de **DHT22** con la **ESP32** como se muestra en la siguente imagen.
![](https://github.com/DanielX834/PRACTICA-N3/blob/main/3Conexion.jpg?raw=true)

 5. Hacer la conexion de **LCD 16x2 (I2C)** con la **ESP32** como se muestra en la siguente imagen.
![](https://github.com/DanielX834/PRACTICA-N3/blob/main/3ConexionL2C.jpg?raw=true)

### Instrucciónes de operación

1. Iniciar simulador.
2. Visualizar los datos en el monitor serial.
3. Colocar la temperatura y humedad dando *doble click* al sensor **DHT22** 

## Resultados

Una vez terminado iniciamos simulacion y se observaran los valores en la lcd.

![](https://github.com/DanielX834/PRACTICA-N3/blob/main/4Resultados.jpg?raw=true)

# Créditos
Desarrollado por Ing. Daniel Armenta


