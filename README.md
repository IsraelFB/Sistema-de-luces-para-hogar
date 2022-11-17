
<h1 align="center"> Sistema de luces para hogar </h1>
<img src="https://user-images.githubusercontent.com/104939556/202371898-a1a6f8b6-ccd4-4dcb-9d05-a50a8984845d.png">
<body>
<p align="center"> 
<b>Instituto Tecnológico de Tijuana </b><br><b>Ingeniería Sistemas Computacionales</b><br><b>Nombre de la Materia: </b><br>Sistemas Programables<br><b>Unidad:</b><br>#3 <br><b>Actividad:</b><br>3.2 Pico W, Webserver con 3 sensores y animación UIX<br><b>Profesor: </b><br>RENE SOLIS REYES<br><b>Alumno(s): </b><br>19211635 Felix Bojorquez Israel <br> 19211707 Perez Ramirez Owen Osvaldo <br> González Gijón Ángel Gabriel <br> Monroy Hernández Emmanuel Emilio <br> Mora Espinosa Michelle Guadalupe <br> <b>Fecha entrega:</b> Jueves 17 de noviembre del 2022
</p>
</body>
<hr>
<b>Introduccion</b><br>
Se describirá el desarrollo para llevar a cabo la actividad,con ayuda de una rasberri pico pi en donde esta fungira como el cerntro de inteligencia que permitira cordinar el funcionamiento de todos los procesos en desarrollo.


<b>Desarrollo</b><br>
<b>Codigo</b><br>
```
#Declaramos las librerias nesesarias 
from machine import Pin, ADC
import utime

#declaramos la variable adc como pin  de entrada para el potenciometro
adc = machine.ADC(machine.Pin(26))

#se declaran los swiches  como pines de entrada en este caso el 2,3 y 4
button1 = Pin(2,Pin.IN)
button2 = Pin(3,Pin.IN)
button = Pin(4,Pin.IN)

#Pines de salida para los led que simularan focos en las habitaciones
ledR=  machine.PWM(machine.Pin(15))
ledG=  machine.PWM(machine.Pin(14))
ledB=  machine.PWM(machine.Pin(13))

#frecuencia de parpadeo de los leds
ledR.freq(1000)
ledG.freq(1000)
ledB.freq(1000)


#Se propgrama un bucle para la lectura constante del potenciometro y reajueste en cuanto a la posicion de algun switch
while True:
    valor=adc.read_u16()

    buttonValue = button.value()
    buttonValue1 = button1.value()
    buttonValue2 = button2.value()

    if buttonValue == 1:
        ledR.duty_u16(valor)
    else:
        ledR.duty_u16(0)

    if  buttonValue1 == 1:
        ledG.duty_u16(valor)
    else:
        ledG.duty_u16(0)

    if  buttonValue2 == 1:
        ledB.duty_u16(valor)
    else:
        ledB.duty_u16(0)
#Esta conversion ayuda a ver el porcentaje del potenciometro que se esta utilizando
    val=valor*100/65535
 
    
#En esta seccion imprimimos los valores de los switch y el porcentaje del potenciometro en uso representando como 1 a un switc encendido o por el contrario  un 0 
    print("Valor potenciometro: " + str(val) +"%"+"  Switc 1: " + str(buttonValue2)+"  Switc 2: " +str(buttonValue1)+" Switc3: " +str(buttonValue))
    utime.sleep(0.1)
    
```
<br><b>Imagenes</b><br>
![image](https://user-images.githubusercontent.com/104939556/202373895-f3ee0bf0-1806-4851-9f39-deeec14b8146.png)
![image](https://user-images.githubusercontent.com/104939556/202374006-40626dd3-e8cc-46bb-9f3f-8434f99b7463.png)
![image](https://user-images.githubusercontent.com/104939556/202374074-39805da8-4e49-4104-a238-3aef4b7f4b8f.png)
![image](https://user-images.githubusercontent.com/104939556/202374120-59d4d9b8-6f59-4cd4-9b6a-ae4a58788c31.png)
![image](https://user-images.githubusercontent.com/104939556/202374265-efd9a3b8-1704-4fea-83a5-af6c1f0eed5d.png)
![image](https://user-images.githubusercontent.com/104939556/202374306-d9f87318-135e-43a0-ba8f-76e848f31241.png)

<b>Prueba en simulador</b><br>
en este simulador se puede verificar el funcionamiento del programa y se muestra el circuito nesesario para poder implementarce en caso de requerisse en un caso real:<br>
https://wokwi.com/projects/348344749806060114
