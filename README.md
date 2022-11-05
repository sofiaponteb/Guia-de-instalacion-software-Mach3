# Guia-de-instalacion-software-Mach3


1. Abra el archivo Mach3VersionR3.041.exe que se encuentra en la ruta ```\Mach3\MACH3 SOFTWARE\Mach3VersionR3.041```

2. Dé click en siguiente hasta instalar el software Mach 3, en la última ventana, **Setup Finished** deje sin seleccionar el ítem ```Load Mach3 Driver```

<p align="center"><img width="400" src="https://github.com/sofiaponteb/Guia-de-instalacion-software-Mach3/blob/main/img/1%20setup%20finished.png"></p>

3. Copie los archivos ```Mach1Lic.dat``` y ```Mach3Mill.xml``` en la ruta ```C:\Mach3```, o donde se encuentre instalado el software

4. Copie los archivos que se encuentran en la carpeta ```plugin files``` en la ruta ```C:\Mach3\PlugIns```

5. Reinicie su equipo para terminar correctamente la instalación

6. En su escritorio encontrará un acceso directo llamado Mach3Mill, este es el software a utilizar

<p align="center"><img width="50" src="https://github.com/sofiaponteb/Guia-de-instalacion-software-Mach3/blob/main/img/2%20acceso.png"></p>

7. Luego de abrir el software, aparecerá una ventana emergente, donde deberá seleccionar el plugin **RnRMotionControllerECO2.0**

8. Conecte la Mach 3 a la unidad USB de su equipo, posteriormente presione el botón rojo de **Reset**, el led incluido en la tarjeta Mach 3 deberá dejar de parpadear y continuar encendido, así como el boton de reset en el software. Si esto no ocurre vuelva a oprimir el botón de reset y espere un momento. 

9. Luego de verificar la lectura de la tarjeta Mach3, puede realizar el montaje del cableado de los motores. El diagrama del cableado utilizado se presenta en el archivo ```Cableado.pdf```. Se recomienda usar una fuente aparte para alimentar la tarjeta Mach 3. Adicionalmente, no debe haber continuidad entre las dos líneas de borneras de la tarjeta, ya que esto la dañaría (El circuito planteado cumple esta condición)

10. Para accionar los motores, encienda las fuentes, y con la tecla ```Tab``` abra la interfaz manual, acá podrá configurar el modo de movimiento: Se recomienda usar Velocity Only para movimientos continuos que se detienen al soltar el mouse y Single step para giros predeterminados luego de cada click. La variable cycle jog step se encuentra dada en mm. Para pruebas iniciales se recomienda la siguiente configuración:


<p align="center"><img width="50" src="https://github.com/sofiaponteb/Guia-de-instalacion-software-Mach3/blob/main/img/3%20software.png"></p>





## Referencias :open_book:
- machsupport.com


## Autora :black_nib:
Ana Sofía Aponte Barriga

Universidad Nacional de Colombia - Sede Bogotá

Ingeniería Mecatrónica
