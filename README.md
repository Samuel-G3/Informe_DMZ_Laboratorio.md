# Informe de configuración de DMZ con Cisco Packet Tracer

## 1. Objetivo del laboratorio

Configurar una DMZ segura usando un router Cisco ISR, aplicando NAT y ACLs para controlar el tráfico entre LAN, DMZ y red externa, asegurando el acceso restringido y la protección de las redes internas.

## 2. Topología implementada

Cantidad de redes: 3  
Dispositivos usados: Router Cisco ISR, PC_Internal (LAN), Server_DMZ, PC_External  

- LAN (192.168.1.0/24): Red interna de usuarios.  
- DMZ (192.168.2.0/24): Zona desmilitarizada donde está alojado el servidor web (192.168.2.10).  
- Red Externa (192.168.3.0/24): Simulación de red pública/internet.  

 
![Captura Packet Tracer topología](https://github.com/user-attachments/assets/e99e4c42-22cd-4c9e-a5f4-e0671ca447ad)

## 3. Plan de direccionamiento IP

| Dispositivo          | IP           | Máscara           | Gateway         |
|----------------------|--------------|-------------------|-----------------|
| PC_Internal          | 192.168.1.10 | 255.255.255.0     | 192.168.1.1     |
| Server_DMZ           | 192.168.2.10 | 255.255.255.0     | 192.168.2.1     |
| PC_External          | 192.168.3.10 | 255.255.255.0     | 192.168.3.1     |
| Router_FW Gi0/0 (LAN)| 192.168.1.1  | 255.255.255.0     | N/A             |
| Router_FW Gi0/1 (DMZ)| 192.168.2.1  | 255.255.255.0     | N/A             |
| Router_FW Gi0/2 (Ext)| 192.168.3.1  | 255.255.255.0     | N/A             |

## 4. Configuración aplicada (resumen)

### Interfaces configuradas con IP:

```bash
interface GigabitEthernet0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown

interface GigabitEthernet0/1
 ip address 192.168.2.1 255.255.255.0
 no shutdown

interface GigabitEthernet0/2
 ip address 192.168.3.1 255.255.255.0
 no shutdown
