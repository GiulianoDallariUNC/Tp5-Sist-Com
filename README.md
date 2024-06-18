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

Ejecutando Driver_gpio.c

El driver esta subido en: https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/tree/main/qemu-rpi-gpio

Al cargar el módulo se setea un sensor por defecto el cual va a enviar los valores al usuario.
![imagen](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/102603446/c0f43ebb-6abc-4e5d-b8d5-d508fc4c908a)


El sensor 1 utiliza los pines 1,2 y 3 y el sensor 2 los pines 4, 5 y 6.

![imagen](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/102603446/902c4598-5d79-4559-9dc3-2905a49da9cb)



El resultado final es un cálculo aleatorio a modo de simular lo que podría ser un valor
sensado real.

Valor obtenido en el sensor 1 es 2 de acuerdo a los valores simulados de los pines.

![imagen](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/102603446/a6965ec0-0b3e-4700-9e63-b779d9825fe0)


Al cambiar uno de los valores de los pines

![imagen](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/102603446/6e59a4aa-a4e9-4246-b12c-ae24614ddde2)


El resultado final varía a 5

![imagen](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/102603446/a701be4f-1129-4466-b355-b023178dfbe3)






## GitLab Adicional: Device Drivers
https://gitlab.com/sistemas-de-computacion-unc/device-drivers
### Driver 1
![imagen](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/82001859/0dff1adc-34a9-4fdd-a696-4e54748d70ef)
![imagen](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/82001859/ce9a78c9-4992-4314-837d-07fe8563bb5d)
### Driver 2
![imagen](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/82001859/ec8650ca-5602-46df-aa16-a2ae7f2b2bb8)
![imagen](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/82001859/8f322297-7002-4504-ad6a-951a4e31ceb5)
<br> En el desarrollo de drivers en Linux, es común trabajar con dispositivos de carácter (character devices). Para gestionar estos dispositivos, se utilizan ciertos tipos y macros definidos en el kernel de Linux, específicamente en el archivo de cabecera *<linux/types.h>*. Uno de estos tipos es dev_t, que es utilizado para representar números de dispositivo.

**dev_t:** Este tipo de dato contiene dos números: el número mayor (major number) y el número menor (minor number). El número mayor identifica al controlador del dispositivo, mientras que el número menor identifica un dispositivo específico controlado por ese controlador.
### Driver 3
![imagen](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/82001859/5a4256a6-3836-4acc-a50d-e0ced362ad12)
![imagen](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/82001859/2170e5db-e1de-4f23-84a2-e54d8a62f6ab)
<br>Probamos utilizar las funciones open, close, read, write que tiene incorporados el driver
![imagen](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/82001859/c1a4b196-38e1-4dde-bae4-a607bb7e3df9)
![imagen](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/82001859/d8c8278f-ecd5-435e-b332-22482eef0065)
![imagen](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/82001859/dc3eddcd-6583-46c6-af2f-b9e6463f5412)
### Driver 4
![imagen](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/82001859/7f95cf40-0dc1-43c9-8363-d9f5984fa7f1)
![imagen](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/82001859/57c2f72e-e19c-49b7-8990-93d0fd867178)
<br>Con el comando *chmod* se le suministran al driver los permisos de lectura/escritura necesarios para su funcionamiento; como este solo posee un búffer de un char, solo almacenará el ultimo caracter recibido. En el primer ejemplo podemos ver como almacenó 't' ya que incluimos el parámetro "-n" en el echo que evita el salto de línea y en el segundo caso donde no lo hicimos, muestra este mismo.
![imagen](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/82001859/839d28db-f244-432e-b729-7fc78881da1d)
### Clipboard
![imagen](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/82001859/7b38cf3c-a2c8-401f-ad0d-c0364b98a25c)
![imagen](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/82001859/c1193c36-3ad3-4a9a-94d8-baa0c6e8ba36)
![imagen](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/82001859/17312c19-df50-46d4-a56d-b74a3cce0c3c)









