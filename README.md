# TP5-Sistemas de Computacion.
Device Drivers  

Alumnos:  
Badariotti, Juan Miguel  
Dallari Larrosa, Gian Franco  
Dallari Larrosa, Giuliano  





## Introducción.


Un "driver" es aquel que conduce, administra, controla, dirige, monitorea la entidad bajo su mando. Un "bus driver" hace eso con un "bus". De manera similar, un "device driver" hace eso con un dispositivo. Un dispositivo puede ser cualquier periférico conectado a una computadora, por ejemplo, un mouse, un teclado, una pantalla/monitor, un disco duro, una cámara, un reloj, etc., cualquier cosa.
Un "driver" puede ser una persona o sistemas automáticos, posiblemente monitoreados por otra persona. Del mismo modo, el "device driver" podría ser una pieza de software u otro periférico/dispositivo, posiblemente controlado por un software. Sin embargo, si se trata de otro periférico/dispositivo, se denomina "device controller" en el lenguaje común. Y por "driver" solo nos referimos a un "software driver". Un "device controller" es un dispositivo en sí mismo y, por lo tanto, muchas veces también necesita un "driver", comúnmente conocido como "bus driver".
Los ejemplos generales de "device controller" incluyen controladores de disco duro, controladores de pantalla, controladores de audio para los dispositivos correspondientes. Ejemplos más técnicos serían los controladores para los protocolos de hardware, como un controlador IDE, un controlador PCI, un controlador USB, un controlador SPI, un controlador I2C, etc.  

## Enunciado.


Para superar este TP tendrán que diseñar y construir un CDD que permita sensar dos señales externas con un periodo de UN segundo. Luego una aplicación a nivel de usuario deberá leer UNA de las dos señales y graficarla en función del tiempo. La aplicación también debe poder indicarle al CDD cuál de las dos señales leer. Las correcciones de escalas de las mediciones, de ser necesario, se harán a nivel de usuario. Los gráficos de la señal deben indicar el tipo de señal que se está sensando, unidades en abscisas y tiempo en ordenadas. Cuando se cambie de señal el gráfico se debe "resetear" y acomodar a la nueva medición.  





## QEMU RPI GPIO:

En esta parte simularemos GPIO Raspberry Pi en qemu.  
El script (qemu-rpi-gpio) interactúa con QEMU utilizando el protocolo qtest incorporado.  
Al envolver el protocolo e interactuar con la memoria del sistema operativo invitado, puede establecer o restablecer los distintos GPIO.  
Para iniciar,forkeamos y clonamos el siguiente repositorio de Github y luego lo compilamos:  
https://github.com/berdav/qemu


![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/b1a3da65-729d-4b38-9026-f028d3120431)


![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/adcf8fbd-aa2f-44cc-8acd-b8c115bb46f3)


![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/f0828b95-3a0a-4494-8998-f498f982ff00)


Una vez clonado el repositorio ejecutamos las instrucciones que se indican:
- mkdir build
- cd build 
- ../configure 
- make

  
Al hacerlo nos encontramos con algunos errores, como se vera a continuacion:  
![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/12a0101c-f7ce-4f00-9c84-a157cd862c40)


Para solucionar este error hicimos lo siguiente:

![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/50e225ac-fdd3-444d-b849-bd7aa2a5857e)


Continuamos con los comandos y obtuvimos el siguiente error:
![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/65c32fc3-c8f2-4b81-b3b3-f7280af38094)


Lo solucionamos con lo siguiente:
![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/2afe79b0-b8af-45f0-a589-04d16fb33943)


Volvimos a ejecutar ../configure
![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/44531334-3f63-4619-bdfb-1a0cd9c6cdc7)


Y esta vez obtuvimos este error:
![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/12413603-eda2-4df7-b6e3-45af56a36e09)


Entonces instalamos libpixman-1:
![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/13be6666-db86-4a04-b95b-c8d7bfe0697c)


Volvimos a ejecutar ../configure:
![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/4af7d416-ec32-4574-82c4-4b7c8b3f6261)


Y ahora el Make:
![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/69324550-77b4-46d3-bf23-e5f015759df1)


Instalamos el script que interactúa con Qemu:  

![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/102603446/cb873735-7f80-40bb-880d-43f0e19d2994)  

Instalamos los prerrequisitos necesarios.
![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/b4f5227c-54ae-46fd-81cb-c90f33bdd64d)
![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/569eb0f8-226c-4683-9f19-b49fb9359067)


Luego descargamos la imagen raspbian usando el comando:  
./qemu-pi-setup/setup.sh  
![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/2a9c8bcb-4cdc-4cdd-be54-3f0ab092a178)


Antes de continuar cambiamos la contraseña y la montamos y guardamos en userconfig:
![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/cfecc668-c26d-460d-a82c-2c9943c5e579)
![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/d7b37a04-a75d-4076-b2e2-91e111c5cd5b)
![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/a2c55487-607f-4513-94bb-5886b0fd9435)


Ahora ejecutamos el script para cargar el socket de unix y hacerlo disponible para qemu
![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/9613818f-8f4c-4b22-9d9c-4826656509dc)  

Ahora verificaremos el funcionamiento de qemu-rpi-gpio  
 Exportamos GPIOs:  
 ![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/c8ea2151-3e85-4805-a407-de2c1a9fc30e)  

Vemos como podemos leer valores de GPIO y tambien setearlos en la shell de qemu:  


![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/9b25f399-bf74-492c-a74c-b7dc28b72704)  

Verificamos el set del GPIO 4 en la Raspberry PI emulada en la otra terminal.  

![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/bdc823aa-611d-4594-9324-374f29f4e088)  

Entonces interactuando desde el terminal de qemu, podemos escribir y leer valores que estan en sys/class/gpio de la Raspberry  
emulada, dandonos acceso desde el userspace a los GPIO.

