# flow4-NodeRed
Este ejercicio hecho en  Node-Red muestra la temperatura, humedad y lo gráfica 

# Introducción

El flow 4 representa el cuarto ejercicio a realizar con NodeRed. Este ejercicio consiste en enviar la temperatura y humedad por medio un nodo mqtt y registrarlas en un cuadro tipo chart

# Material Necesario
Para realizar este flow necesitas lo siguiente:

1. Ubuntu 20.04
2. NodeJS
* NPM
* NodeRed
* Nodos Dashboard

# Material de referencia
En los siguientes enlaces puedes encontrar cursos en la plataforma de edu.codigoiot.com que te permitirán realiar las configuraciones necesarias

* [Instalación de Virtual Box y Ubuntu 20.04](https://edu.codigoiot.com/course/view.php?id=812)
* [Instalación de NodeRed](https://edu.codigoiot.com/enrol/index.php?id=817)
* [Introducción a NodeRed](https://edu.codigoiot.com/enrol/index.php?id=278)
* [Introducción a MQTT](https://edu.codigoiot.com/course/view.php?id=851)

# Instrucciones
## Requisitos previos
Para que este flow funcione, debes cumplir con los siguientes requisitos previos

1. Instalación de NodeJS. Se recomienda tener instalado NodeJS en alguna versión LTS. Al momento de creación de este documento, se usó la versión 16.17LTS. Esta instalación debe incluir las Build-Tools para hacer uso de NPM

2. Instalación de NodeRed. La instalación se realiza por NPM. Al momento de la creación de este contenido, se usó la versión 3.0.2


# Instrucciones de preparación del entorno
Para ejecutar este flow, es necesario lo siguiente

1. Arrancar NodeRed con el comando node-red
2. Añadir los siguientes nodos:
   * 1 nodo tipo mqtt in 
   * 1 nodo tipo json
   * 2 nodos tipo function
   * 2 nodos tipo gauge
   * 1 nodo tipo chart

nota: para ver las conexiones de los nodos dirigirse al apartado de resultados que se encuentra mas abajo

3. Modificar el nombre del servidor del nodo mqtt a localhost:1883 y su topic a codigoIoT/Mor/mqtt/flow4
4. Cambiar la propiedad del nodo tipo json para que siempre convierta a objetos Javascript
5. Cambiar el nombre del 1° nodo function a Temperatura y añadir el siguiente codigo en la pestaña on message: 
    msg.payload = msg.payload.temp;
    msg.topic = "Temperatura";
    return msg;

6. Cambiar el nombre del 2° nodo function a Humedad y añadir el siguiente codigo en la pestaña on message: 
    msg.payload = msg.payload.hum;
    msg.topic = "Humedad";
    return msg;

7. Agregar una nueva tabla en el dashboard de nombre flow4 y añadir 3 grupos dentro de ella con los nombres de Temperatura, Humedad e Historico, dar clic en los nodos de temperatura, humedad e historico y asociarlos con los grupos creados
8. Modificar los rangos de los nodos de temperatura y humedad de minimo a maximo
9. Hacer clic en el boton Deploy

# Instrucciones de operación
Para observar el resultado de este flow, sólo es necesario abrir en otra pestaña del navegador la direccion http://localhost:1880/ui y seleccionar el flow4, posteriormente en una terminal nueva de ubuntu mandar la siguiente instrucción: mosquitto_pub -h localhost -t codigoIoT/Mor/mqtt/flow4 -m '{"id":"Daniel Rochez","temp":25,"hum":58}' esto hara que se envie información al dashboard

# Resultados
A continuación puede verse una vista previa del resultado de este flow.
Resultados

Diagrama de nodos 
![Cargando](https://github.com/DanielRochez/flow4-NodeRed/blob/main/imagen5.png?raw=true)

Resultado en pantalla
![Cargando](https://github.com/DanielRochez/flow4-NodeRed/blob/main/imagen6.png?raw=true)

# Evidencias
https://user-images.githubusercontent.com/111370727/188023767-29d36482-2100-4597-8844-d6a79e83a926.mp4

# Créditos
Desarrollado por Daniel Rochez

* [GitHub](https://github.com/DanielRochez)
