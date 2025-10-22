# Laboratorio-4
Red y Máquinas Virtuales
--
**Autores:**  
Marco Antonio Gómez — Juan Pablo Pedraza — Carlos Manuel Guevara  
**Fecha:** 21 de octubre de 2025

---

##  Descripción General

Este laboratorio tuvo como objetivo **configurar un switch Cisco** para establecer la comunicación entre distintos dispositivos (PC, Raspberry Pi y otros hosts), implementando una **VLAN** y validando la conectividad mediante herramientas como `ping` y `nmap`.

---

##  Configuración del Switch

1. **Acceso al modo privilegiado y de configuración global:**
   ```bash
   enable
   configure terminal
   ```
2. **Cambio de nombre del dispositivo:**
   ```bash
   hostname Gatitos
   ```
3. **Creación y configuración de la VLAN 10:**
   ```bash
   vlan 10
   name Marco
   interface vlan 10
   ip address 192.168.10.1 255.255.255.0
   no shutdown
   ```
4. **Asignación de puertos a la VLAN 10:**
   ```bash
   interface range fa0/1 - 10
   switchport mode access
   switchport access vlan 10
   ```
5. **Verificación y guardado:**
   ```bash
   show vlan brief
   show ip interface brief
   write memory
   ```

---

##  Conexión de Dispositivos

- **Configuración en Ubuntu / Raspberry Pi:**
  - IP asignada: `192.168.10.2`
  - Comprobación con `ip a` mostró conectividad activa vía cable Ethernet.

- **Prueba de conectividad:**
  ```bash
  ping 192.168.10.1
  ```
  Resultado: 100% de éxito, tiempos promedio de 4 ms.

---

##  Pruebas de Red

- **Escaneo con Nmap al switch (192.168.10.1):**
  - Puertos abiertos: `22 (SSH)`, `23 (Telnet)`, `80 (HTTP)`, `443 (HTTPS)`.

- **Escaneo a otro host (192.168.10.3):**
  - Solo puerto `22/tcp` abierto (SSH habilitado).

- **Comprobación de interfaces activas en el switch:**
  ```bash
  show ip interface brief
  ```
  Interfaces `Vlan1` y `Vlan10` activas.

---

##  Configuración SSH

- Se instaló y habilitó el servicio SSH en Ubuntu.  
- Se verificó la conexión remota exitosa mediante intercambio de claves y autenticación.  
- Se transfirió un archivo entre equipos usando `scp`.

---

## Resultados

- Se estableció comunicación entre PC, Raspberry y switch.  
- VLAN 10 configurada correctamente.  
- Conectividad validada con `ping` y `nmap`.  
- Acceso remoto mediante SSH operativo.  

