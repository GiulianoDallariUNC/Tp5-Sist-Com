# Tp5-Sist-Com
Trabajo final Sistemas de Computacion 2024

QEMU RPI GPIO:

En esta parte simularemos GPIO Raspberry Pi en qemu,
El script (qemu-rpi-gpio) interactúa con QEMU utilizando el protocolo qtest incorporado.
Al envolver el protocolo e interactuar con la memoria del sistema operativo invitado, puede establecer o restablecer los distintos GPIO.

![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/b1a3da65-729d-4b38-9026-f028d3120431)


![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/adcf8fbd-aa2f-44cc-8acd-b8c115bb46f3)


![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/f0828b95-3a0a-4494-8998-f498f982ff00)


Una vez clonado el repositorio ejecutamos las instrucciones que se indican:
 - mkdir build
 - cd build 
- ../configure 
- make 
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
![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/b4f5227c-54ae-46fd-81cb-c90f33bdd64d)
![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/569eb0f8-226c-4683-9f19-b49fb9359067)


Luego descargamos la imagen raspbian usando el comando: ./qemu-pi-setup/setup.sh
![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/2a9c8bcb-4cdc-4cdd-be54-3f0ab092a178)


Antes de continuar cambiamos la contraseña y la montamos y guardamos en userconfig:
![image](https://github.com/GiulianoDallariUNC/Tp5-Sist-Com/assets/147262273/cfecc668-c26d-460d-a82c-2c9943c5e579)


