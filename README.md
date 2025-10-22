# Laboratorio-4
Red y Máquinas Virtuales
--
**Autores:**  
Marco Antonio Gómez — Juan Pablo Pedraza — Carlos Manuel Guevara  
**Fecha:** 21 de octubre de 2025

---

##  Descripción General

En este laboratorio se realizó la **configuración de un switch Cisco** para permitir la comunicación entre diferentes dispositivos conectados en red (como una PC y una Raspberry Pi).  
El objetivo principal fue implementar una **VLAN (Red de Área Local Virtual)**, asignar direcciones IP a cada dispositivo y verificar la conectividad mediante pruebas de red.

---

##  Configuración del Switch

Primero, se accedió al **modo privilegiado** y luego al **modo de configuración global** del switch.  
Se cambió el nombre del dispositivo a *“Gatitos”* para identificarlo fácilmente dentro de la red.

Posteriormente, se **creó la VLAN 10**, asignándole el nombre *“Marco”*.  
A esta VLAN se le configuró una **dirección IP** correspondiente al segmento 192.168.10.0/24, y se activó su interfaz virtual para que pudiera funcionar como **puerta de enlace** (gateway) de los dispositivos conectados.

Después, se seleccionó el rango de **puertos físicos** del switch (del 0/1 al 0/10), configurándolos como **puertos de acceso** y asignándolos a la VLAN 10.  
Finalmente, se guardaron los cambios y se verificó el estado de las interfaces y las VLAN activas para confirmar que la configuración fue exitosa.

---

##  Conexión de Dispositivos

Se conectaron una **PC (Ubuntu)** y una **Raspberry Pi** al switch, asignándoles direcciones IP dentro de la misma subred (por ejemplo, 192.168.10.2).  
Se comprobó la conectividad de red observando que la interfaz Ethernet estaba activa y enlazada correctamente con el switch.

Mediante una prueba de *ping* hacia la dirección del switch (192.168.10.1), se confirmó la comunicación exitosa, con una tasa de respuesta del 100% y tiempos de transmisión promedio de 4 ms.  
Esto demostró que tanto la VLAN como la conexión física estaban correctamente configuradas.

---

##  Pruebas de Red

Se realizaron pruebas de exploración de red con **Nmap** para analizar los servicios activos y la apertura de puertos:

- En el **switch**, se detectaron los servicios SSH, Telnet, HTTP y HTTPS disponibles.  
- En otro dispositivo dentro de la red, solo se encontró abierto el puerto SSH, lo cual indica que el equipo estaba configurado para administración remota segura.

Además, se verificó que las **interfaces VLAN1 y VLAN10** del switch estuvieran activas, mientras que la mayoría de las interfaces físicas no estaban en uso.

---

##  Configuración del Servicio SSH

Se instaló y configuró correctamente el servicio **SSH** en el sistema Ubuntu, permitiendo el acceso remoto seguro desde otros dispositivos de la red.  
Durante las pruebas se aceptó la huella digital del host remoto, se autenticó la conexión con contraseña y se realizó exitosamente una **transferencia de archivos** mediante un canal seguro.

---

##  Resultados Obtenidos

- El switch Cisco fue configurado correctamente con una VLAN funcional.  
- Se logró establecer comunicación entre los dispositivos conectados.  
- Las pruebas de conectividad y exploración confirmaron el buen funcionamiento de la red.  
- El acceso remoto mediante SSH operó sin errores. 
