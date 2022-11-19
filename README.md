# Guia-de-uso-software-Mach3

## Contenido:

1. [Instalación Software Mach3](#instalación-software-mach3)
2. [Uso Software Mach3](#uso-software-mach3)
     1. [Configurar Velocidad de los motores](#configurar-velocidad-de-los-motores)
     2. [Configurar eje A como eje esclavo de Z](#configurar-eje-a-como-eje-esclavo-de-z)
     3. [Configurar entradas para utilizar finales de carrera y parada de emergencia](#configurar-entradas-para-utilizar-finales-de-carrera-y-parada-de-emergencia)
     4. [Configurar salidas para encender y apagar la antorcha y la válvula](#configurar-salidas-para-encender-y-apagar-la-antorcha-y-la-válvula)


## Instalación Software Mach3

1. Abra el archivo Mach3VersionR3.041.exe que se encuentra en la ruta ```\Mach3\MACH3 SOFTWARE\Mach3VersionR3.041```

2. Dé click en siguiente hasta instalar el software Mach 3, en la última ventana, **Setup Finished** deje sin seleccionar el ítem ```Load Mach3 Driver```

<p align="center"><img width="400" src="https://github.com/sofiaponteb/Guia-de-instalacion-software-Mach3/blob/main/img/1%20setup%20finished.png"></p>

3. Copie los archivos ```Mach1Lic.dat``` y ```Mach3Mill.xml``` en la ruta ```C:\Mach3```, o donde se encuentre instalado el software

4. Copie los archivos que se encuentran en la carpeta ```plugin files``` en la ruta ```C:\Mach3\PlugIns```

5. Reinicie su equipo para terminar correctamente la instalación

6. En su escritorio encontrará un acceso directo llamado Mach3Mill, este es el software a utilizar

<p align="center"><img width="70" src="https://github.com/sofiaponteb/Guia-de-instalacion-software-Mach3/blob/main/img/2%20acceso.png"></p>

7. Luego de abrir el software, aparecerá una ventana emergente, donde deberá seleccionar el plugin **RnRMotionControllerECO2.0**

8. Conecte la Mach 3 a la unidad USB de su equipo, posteriormente presione el botón rojo de **Reset**, el led incluido en la tarjeta Mach 3 deberá dejar de parpadear y continuar encendido, así como el boton de reset en el software. Si esto no ocurre vuelva a oprimir el botón de reset y espere un momento. 

9. Luego de verificar la lectura de la tarjeta Mach3, puede realizar el montaje del cableado de los motores. El diagrama del cableado utilizado se presenta en el archivo ```Cableado.pdf```. Se recomienda usar una fuente aparte para alimentar la tarjeta Mach 3. Adicionalmente, no debe haber continuidad entre las dos líneas de borneras de la tarjeta, ya que esto la dañaría (El circuito planteado cumple esta condición)

10. Para accionar los motores, encienda las fuentes, y con la tecla ```Tab``` abra la interfaz manual, acá podrá configurar el modo de movimiento: Se recomienda usar Velocity Only para movimientos continuos que se detienen al soltar el mouse y Single step para giros predeterminados luego de cada click. La variable cycle jog step se encuentra dada en mm. Para pruebas iniciales se recomienda la siguiente configuración:


<p align="center"><img width="400" src="https://github.com/sofiaponteb/Guia-de-instalacion-software-Mach3/blob/main/img/3%20software.png"></p>

## Uso Software Mach3

A continuación se presentan algunas configuraciones a realizar en el software para un uso adecuado del mismo con el dispositivo de soldadura.

### Configurar Velocidad de los motores

Dé click en la opción ```Config > Motor Tuning```, en la columna de la derecha seleccione el motor que desea configurar y en la parte inferior digite los valores que desea en cada ítem, se recomienda la siguiente configuración:
 - Steps:
 - Velocity:
 - Acceleration:

 Al finalizar la configuración de cada eje dé click en el botón **Save Axis Settings**, cuando acabe la configuración de todos los motores dé click en el botón **OK**

<p align="center"><img width="400" src="https://github.com/sofiaponteb/Guia-de-instalacion-software-Mach3/blob/main/img/velconfig.png"></p>

### Configurar eje A como eje esclavo de Z

En este caso se requiere el uso de dos motores para asegurar el adecuado movimiento del eje Z, es por eso que se realiza la conexión del motor denominado A en la configuración de pines de la tarjeta Mach3. El motor A se configura de la siguiente forma para que realice movimientos sincrónicos con el eje Z (configuración del eje A como esclavo de Z):

Dé click en la opción  ```Config > Slave Axis``` y seleccione la opción **A** en la columna del eje **Z**. De esta forma A se convierte en esclavo de Z, esto quiere decir que cuando el eje Z se mueve, el eje A se mueve en sincronía con el eje Z.

<p align="center"><img width="400" src="https://github.com/sofiaponteb/Guia-de-instalacion-software-Mach3/blob/main/img/slaveAxis.png"></p>

### Configurar entradas para utilizar finales de carrera y parada de emergencia

Los finales de carrera y la parada de emergencia se conectan según el diagrama incluido en el path ```\Mach3\Cableado.pdf```

Seleccione la opción ```Config > Ports and Pins > Input Signals```.

**Parada de emergencia**

La parada de emergencia se conectará a la entrada 1 de la tarjeta Mach3.

Desplácese hacia abajo en la tabla hasta encontrar la opción **EStop**, asegúrese de que tiene marcada la opción ```Enabled``` e ingrese los siguientes valores:
- Port #: 3. Se refiere a la tarjeta Mach3
- Pin Number: 1. Se refiere a la entrada número 1 (**IN1**) de la tarjeta

<p align="center"><img width="400" src="https://github.com/sofiaponteb/Guia-de-instalacion-software-Mach3/blob/main/img/EStop.png"></p>

**Finales de carrera**

Los finales de carrera se conectarán de forma paralela en la entrada 2 de la tarjeta Mach3.

Desplácese hacia arriba en la tabla hasta encontrar las opciones:
**X++, X--, Y++, Y--, Z++, Z--** asegúrese de que tienen marcada la opción ```Enabled``` e ingrese los siguientes valores:
- Port #: 3. Se refiere a la tarjeta Mach3
- Pin Number: 2. Se refiere a la entrada número 2 (**IN2**) de la tarjeta

<p align="center"><img width="400" src="https://github.com/sofiaponteb/Guia-de-instalacion-software-Mach3/blob/main/img/finalescarrera.png"></p>

### Configurar salidas para encender y apagar la antorcha y la válvula

Se usará la salida **OUT1** para activar el relé de la antorcha y la salida **OUT2** para activar el relé de la válvula.

Seleccione la opción ```Config > Ports and Pins > Spindle Setup```. Desactive la salida PWM e ingrese los siguientes valores:
- Clockwise Output #: 1
- Mist Output #: 2

En el Gcode se usarán los siguientes códigos:
- **M3:** Encender antorcha
- **M5:** Apagar antorcha
- **M7:** Encender válvula
- **M9:** Apagar válvula

<p align="center"><img width="400" src="https://github.com/sofiaponteb/Guia-de-instalacion-software-Mach3/blob/main/img/salidas.png"></p>

## Referencias :open_book:
- machsupport.com


## Autora :black_nib:
Ana Sofía Aponte Barriga

Universidad Nacional de Colombia - Sede Bogotá

Ingeniería Mecatrónica
