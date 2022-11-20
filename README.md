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
Como se ha visto en la primera parte del curso, el procesamiento de imágenes realiza muchas transformaciones de la información contenida de una imagen digital y esto se traduce en cambios que nos permiten visualizar, corregir, mejorar, cambiar o extraer los datos de intensidad de color en las dichas imágenes.
Hemos visto también que el procesamiento de las imágenes se da en varias etapas y cada etapa es importante porque en cada una de ellas se mejorar la información que se está tratando. En Los sistemas de PDI (o sistemas de visión artificial) las etapas más importantes son la adquisición, el preprocesado, la segmentación, el reconocimiento y la descripción de la imagen. En esta práctica abordaremos la etapa de adquisición de imagen digitales programando un circuito que nos permita obtener imágenes digitales que se enviaran a un servidor web y a las que podremos acceder vía WiFi o vía streaming.


### Material Necesario
-	Microcontrolador ESP32 CAM con cámara OV2640 <img src="https://media.giphy.com/media/WUlplcMpOCEmTGBtBW/giphy.gif" width="50">
-	Circuito convertidor USB-TTL <img src="https://media.giphy.com/media/WUlplcMpOCEmTGBtBW/giphy.gif" width="50">
-	Cable de datos USB-USB mini <img src="https://media.giphy.com/media/WUlplcMpOCEmTGBtBW/giphy.gif" width="50">
-	Cable de red <img src="https://media.giphy.com/media/WUlplcMpOCEmTGBtBW/giphy.gif" width="50">
-	Computadora <img src="https://media.giphy.com/media/WUlplcMpOCEmTGBtBW/giphy.gif" width="50">
-	Modem (se conectará el esp32 con SSID y el password del modem) <img src="https://media.giphy.com/media/WUlplcMpOCEmTGBtBW/giphy.gif" width="50">
