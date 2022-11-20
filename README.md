<h1 align="center"> <a href="https://www.unitec.mx">UNIVERSIDAD TECNOLÓGICA DE MÉXICO</h1> </a>
 <h3 align="center"> Procesamiento Digital de imagenes </h3></a>
 <br>
<img align='right' src="https://github.com/ferhs343/Servidor-web-con-el-ESP32-CAM/blob/main/clipart4611933.png" width="330">
<p><em>La presente práctica tiene como objetivo analizar e implementar el uso del microcontrolados ESP32CAM con la finalidad de utlizarlo mediante el IDE de Arduino, asi como phyton para capturar y visualizar imágenes y videos.</p></em>

<h2> Integrantes <img src="https://media.giphy.com/media/WUlplcMpOCEmTGBtBW/giphy.gif" width="50"></h2>

- <p align="left">🧑‍💻 <a href="https://github.com/Fernand0Guzman">Luis Fernando Guzmán Licona</p> </a>
- <p align="left">🧑‍💻 <a href="https://www.github.com/ferhs343">Luis Fernando Herrera Serrano</p> </a>
- <p align="left">🧑‍💻 <a href="https://www.github.com/pabloolivos">Pablo Gerardo Olivos Guerrero</p> </a>
- <p align="left">🧑‍💻 <a href="https://www.github.com/israelu">Israel Uzan Martínez</p> </a>

### Introducción 
------------
Como se ha visto en la primera parte del curso, el procesamiento de imágenes realiza muchas transformaciones de la información contenida de una imagen digital y esto se traduce en cambios que nos permiten visualizar, corregir, mejorar, cambiar o extraer los datos de intensidad de color en las dichas imágenes.
Hemos visto también que el procesamiento de las imágenes se da en varias etapas y cada etapa es importante porque en cada una de ellas se mejorar la información que se está tratando. En Los sistemas de PDI (o sistemas de visión artificial) las etapas más importantes son la adquisición, el preprocesado, la segmentación, el reconocimiento y la descripción de la imagen. En esta práctica abordaremos la etapa de adquisición de imagen digitales programando un circuito que nos permita obtener imágenes digitales que se enviaran a un servidor web y a las que podremos acceder vía WiFi o vía streaming.


### Material Necesario
------------
-	Microcontrolador ESP32 CAM con cámara OV2640 <img src="https://github.com/ferhs343/Servidor-web-con-el-ESP32-CAM/blob/main/esp.png" width="60">
-	Circuito convertidor USB-TTL <img src="https://media.giphy.com/media/WUlplcMpOCEmTGBtBW/giphy.gif" width="50">
-	Cable de datos USB-USB mini <img src="https://github.com/ferhs343/Servidor-web-con-el-ESP32-CAM/blob/main/usb.png" width="50">
-	Cable de red <img src="https://github.com/ferhs343/Servidor-web-con-el-ESP32-CAM/blob/main/utp.png" width="55">
-	Computadora <img src="https://github.com/ferhs343/Servidor-web-con-el-ESP32-CAM/blob/main/ClutteredSimpleKissingbug-max-1mb.gif" width="50">
-	Modem (se conectará el esp32 con SSID y el password del modem) <img src="https://github.com/ferhs343/Servidor-web-con-el-ESP32-CAM/blob/main/modem.png" width="65">

### Software necesario
------------
El software se instalará en la computadora donde conectaremos nuestro ESP32 CAM. Respetar la versión del software que se indica para evitar conflictos entre las bibliotecas.  
-  IDE de Arduino 1.8.19
- Drivers (Windows) para el esp32 cam (se comparte en el material semanal)
- IDE de Python (se recomienda la versión 3.7 de Python)
	- La biblioteca OpenCv para python versión 4.2.x
- Bibliotecas de Arduino para el manejo del esp32 CAM
	- https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json  (en preferencias-- Gestor de URLS)
	- Instalar en el <gestor de tarjetas del IDE de Arduino> la tarjeta ESP32 de Expressif Systemas
	- La biblioteca CameraWebServer de los ejemplos para la ESP32 CAM de AI Thinker
	- Navegador web 

### Desarrollo.
------------
Para poder visualizar las imágenes y vídeo capturadas con la cámara del ESP32 CAM es necesario crear un servidor web, el procedimiento descrito a continuación nos permitirá crear el servidor web para visualizar en un navegador y en Python las imágenes y vídeo.
1. Descargar e Instalar el IDE de Arduino 1.18.19 de la página oficial   https://www.arduino.cc/en/software
 ![image](https://user-images.githubusercontent.com/114788305/202881122-519d0e26-3ef9-4209-84ba-b8ce0c81853d.png)

2. Instalar los drivers para establecer la conexión serial entre el circuito de la ESP32 CAM y la computadora. Los drivers son los CH34x para Windows. Si se instala en Linux no es necesario instalarlos ya que vienen por default.
3. Dar de alta la tarjeta ESP32 cam en el IDE de Arduino en el menú archivo >> preferencias y el campo de gestor de URLS adicionales escribir 
https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json 

![image](https://user-images.githubusercontent.com/114788305/202881124-0f4f97fe-f423-453c-95fd-3fa958ec6506.png)

4. En el IDE de Arduino ir a Herramientas>> Placa >> Gestor de tarjetas, buscar la placa ESP32 CAM de Expressiff Systems e instalarla. En caso de que no aparezca la placa revisar el paso anterior. 
 
![image](https://user-images.githubusercontent.com/114788305/202881129-0939341c-50b1-42b5-b20c-2e2e506afe1c.png)
![image](https://user-images.githubusercontent.com/114788305/202881130-f46f042c-fcf2-4785-802e-eaade15ced00.png)

5. Después de instalar la tarjeta hay que elegir la placa ESP32 de AI Thinker para poder programarla, se elige en el menú herramientas >> placa >> ESP32 arduino >> AI Thinker ESP32-CAM. Al finalizar hay que conectar la placa al puerto USB.

![image](https://user-images.githubusercontent.com/114788305/202881134-34bdee34-f2b6-4a17-ac79-cfa8c57b037f.png)

6. Una vez configurada la placa se debe revisar que haya comunicación serial entre el dispositivo y la computadora, por lo que hay que tener conectada el ESP32 a la computadora, para esto hay que ir al menú herramientas >> monitor serie. Otra forma de saber si hay comunicación es revisar si hay puerto disponible en el menú >> puerto, si aparece un puerto habilitado es indicio de que hay comunicación. Al momento de revisar la comunicación con la primera opción hay que colocar la velocidad del monitor serial en 9600 o 115600 baudios para obtener texto que indique la comunicación. Dado que estamos usando la placa ESP32 con el convertidor usb-ttl sólo es necesario oprimir el botón de download o reset para saber si está comunicándose con la computadora. 
 
![image](https://user-images.githubusercontent.com/114788305/202881136-b8e4a886-ef63-4c32-acb5-6d730f79c48e.png)

	
7. Establecida la comunicación serial entre el ESP32 y la computadora procedemos a cargarle el programa que nos permite crear el servidor web para tomar imágenes y vídeo, para esto abriremos el programa que se encuentra en Archivo >> Ejemplos >> ESP32 >> Camera >> CameraWebServer
 ![image](https://user-images.githubusercontent.com/114788305/202881138-daa5ca35-4ecf-4819-9972-ce84498abeae.png)

El programa aparecerá cargado en el editor de código de Arduino, antes de cargarlo hay que configurarlo.
8. Antes de cargar el código a la tarjeta debemos definir el tipo de cámara que estamos usando (en nuestro caso es CAMERA_MODEL_AI_THINKER) y colocar el nombre de la red wifi a la que nos conectaremos con el ESP32 CAM (aquí prendemos el modem y conectamos la computadora al mismo con el cable de red) y el password de la red.

![image](https://user-images.githubusercontent.com/114788305/202881141-7fbd0131-2960-4b03-a236-cb1ed96600c7.png)

9. Realizado lo anterior nos cercioramos que este conectado el ESP32 al puerto USB. Abrimos el monitor serial para revisar el status de la compilación y subida del código, oprimimos el botón de reset del ESP32 CAM una vez y subimos el código a la placa usando el botón subir. Esto comenzará a programar el ESP32, tardará unos segundos 

![image](https://user-images.githubusercontent.com/114788305/202881145-2bda5689-783c-4306-bad3-f372761e1b05.png)

 10. Al finalizar la programación del ESP32 en el monitor serial debemos ver un mensaje como el siguiente
 
	![image](https://user-images.githubusercontent.com/114788305/202881151-2526bc91-719f-4c49-b0d7-654c918e6cbe.png)

Del mensaje anterior nos interesa la última línea que nos informa la dirección IP donde podemos visualizar las imágenes de la cámara web del ESP32 CAM
Camera Ready! Use ‘http://192.168.x.xx’ to connect
Copiamos y pegamos la dirección en un navegador web y ya tendremos listo nuestro servidor para recibir imágenes y vídeo del microcontrolador ESP32 CAM.
En el navegador se deberá ver algo parecido a esto, una pagina con los controles para iniciar streaming de vídeo o captura de imágenes. Para comenzar el streaming pulsa el botón de start streaming.
 ![image](https://user-images.githubusercontent.com/114788305/202881166-40758a78-2395-446a-9f46-8c48f3710b61.png)

10. Una de las características del servidor es que podemos exportar las imágenes para realizar alguna otra aplicación. En esta parte realizaremos un ejemplo de cómo hacer la exportación de imágenes a Python y OpenCv desde el servidor. 
•	Anaconda Navigator  https://www.anaconda.com/ 
•	Al finalizar la instalación de Anaconda instalamos, usando el prompt de Anaconda ejecutado como administrador, la versión 4.4.0.46 de OpenCv usando el comando  pip install opencv-contrib-python==4.4.0.46

![image](https://user-images.githubusercontent.com/114788305/202881169-e92b6b6d-fc7b-4a92-8e9b-56f847a7f93f.png)

•	Abrimos el editor de código de Spyder y pegamos el siguiente código

import cv2
from urllib.request import urlopen
import numpy as np
 
stream = urlopen('http://192.168.xx.x:81/stream') # En esta línea pegar la dirección
bytes = bytes()
while True:
    bytes += stream.read(1024)
    a = bytes.find(b'\xff\xd8')
    b = bytes.find(b'\xff\xd9')
    if a != -1 and b != -1:
        jpg = bytes[a:b+2]
        bytes = bytes[b+2:]
        if jpg :
            img = cv2.imdecode(np.fromstring(jpg, dtype=np.uint8), cv2.IMREAD_COLOR)
            cv2.imshow('ESP32 CAM', img)
    if cv2.waitKey(1) & 0xff == ord('q'):
        break
stream.release()
cv2.destroyAllWindows()

En la línea correspondiente a la variable stream pegamos la dirección que nos arrojó el monitor serial para visualizar las imágenes del ESP32 CAM. Con lo anterior ya estamos usando imágenes obtenidas de nuestro microcontrolador.


### Resultados
------------


### Conclusiones
------------
<p align="justify"> Una vez concluida la presente práctica “ESP-32CAM” se adquirió  conocimiento teórico como práctico acerca del análisis, configuración  y uso del microcontrolador. Como primer punto, se configuró la PC que  se usaría para la programación y uso del microcontrolador, dicha  configuración implicó la instalación de drivers del ESP y el IDE de  Arduino en su versión 1.8.19. Después de tener listo el equipo de  cómputo, se prosiguió a instalar las dependencias y librerías para el  microcontrolador, así como la ejecución del código ejemplo ESP-32,  como resultado nos arrojaría una dirección IP de manera local en la  cual se podría ver la transmisión de la cámara. Si bien es cierto, en  nuestro equipo tuvimos inconvenientes con el dispositivo, el cual fue  la tarjeta programador ya que nuestro pc no lograba establecer  conexión con la dirección local, pero gracias al uso de otro  microcontrolador logramos obtener los resultados esperados. En  síntesis, fue una práctica muy completa y enriquecedora en los  aspectos planteados. - Israel Uzan Martínez </p></a>
	


### Carpeta con los códigos usados
------------


### Evidencias de la práctica
------------



