# Wibeee Smilics & Circutor API Local XML

![Wibeee_Smilics_Circutor](https://user-images.githubusercontent.com/19588354/130455986-a089c538-e672-45fc-9eec-ccb2498071fb.jpg)


Wibeee-Smilics-API-Local: Recopilación de datos del dispositivo usando la conexión http puerto 80 en modo local, para integrar en nuestra BBDD InfluxDB 2.0

Wibeee y Smilics ambos son dispositivos muy parecidos, sólo que marcas diferentes, uno es de la empresa Circutor y Smilics digamos de la marca hija, la comunicación es ModBus con un lenguaje XML. Wibeee es un analizador de consumo con conexión inalámbrica vía Wifi, muestra los datos instantáneos e històricos del consumo eléctrico mediante cualquier dispositivo Inteligente, Tablet o PC, con ayuda de su app o del servidor web integrado, que si realizamos un escaneo de red local, podremos encontrar la dirección IP que se encuentra asignada. 
Wibeee es muy fácil de instalar, en tan solo unos pocos segundos está montado. Siempre y cuando los recursos necesarios estén correctamente. 

Bien, los datos que se van a recopilar del dispositivos no serán por medio de la pagina web oficial, sino vamos a obtenerlos directamente del dispositivo, mediante una solicitud HTTP REQUEST API en formato XML (Lo que es lo mismo lenguaje de marcas), se realizará con las siguiguientes herramientas necesarias y sin coste adicionadl siempre y cuando utilicen su propio PC o Portatil, en caso de querer recopilar los datos de forma continua les recomiendo usar un dispositivo llamado RaspberryPi o bien una NAS, para aquellos que necesiten más información o desconozcan los recursos, pueden ponerse en contacto.

Bien el software que usaremos y que entiendo para aquellos que han trabajado con ello, empezaré en base partir de los recursos necesarios tanto de hardware cómo software:

1. NAS, PC, RaspberryPi2, o máquina Virtual instalada en vuestro equipo.
2. Node-RED, InfluxDB 2.0 y Grafana. (Es necesario tener instalado el sistema operativo Linux, da igual el tipo de Linux). Docker en el caso de si desean utilizar los repositorios existentes, (recomendado).

![Esquema_Node_Red_Wibeee_Circutor](https://user-images.githubusercontent.com/19588354/130483044-a82787c8-0236-4ffe-99d7-9dbed69c2c89.jpg)
![Esquema_InfluxDB2 0_Wibeee_Circutor](https://user-images.githubusercontent.com/19588354/130484463-0f3d7e45-73d9-48ad-96e8-e9fe3408e90f.jpg)



Bien una vez tengamos todas las herramientas y nuestro hardware listo, podremos iniciar la preparación del código en NodeRed y cómo poder recopilar los datos de nuestro dispositivo LOCAL, sin tener que usar la página web oficial de https://wibeee.circutor.com o https://smilics.com/wibeee

El propio dispositivo recopila información cómo decía antes en formato XML mediante una dirección similar a esta:

http://192.168.1.3/en/status.xml

Bien y aparece un listado muy extenso, depende del modelo de Wibeee, porque existe con firmware antiguos del 20216 con menos detalles que los actuales.

Estos datos vamos aprender cómo recopilarlos y obtenerlos desde Node-RED que es una de las herramientas más útilices hoy en día de software libre.

La solicitud que se utilizan es REST que quiere decir que recope esa información y una vez obtenida con esta solicitud, nos ayudará a poder transformar esos datos con una función personalizada para así enviarla a nuestra BBDD InfluxDB 2.0 (Existen versiones anteriores, pero en este caso se realizará con la más actualizada). Estos scripts nos ayudan a coger los datos de varios dispositivos Wibeee con los siguientes métodos: modbus y HTTP XML y guardarlos en una base de datos MySQL o InfluxDB para luego poder tratarlos o visializarlos en Grafana, sin necesidad de enviar nuestros datos a aplicaciones externas, cómo es en este caso http://wibeee.circutor.com o https://smilics.com/wibeee.

Con esto conseguimos una monitorización mucho más real e instantanea para tomar decisiones de nuestros consumos en casa, y no tener que guardar nuestra información en las aplicaciones de terceros que suelen tener un retardo de 1 a 5 min. Dependiendo del dispositivo o fabricante.
