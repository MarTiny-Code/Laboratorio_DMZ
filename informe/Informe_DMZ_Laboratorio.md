
# Informe Técnico: Implementación de DMZ Segura

## 1. Introducción
El objetivo de este laboratorio es configurar una Zona Desmilitarizada (DMZ) para alojar un servidor web accesible desde Internet, manteniendo la red interna (LAN) aislada y protegida.

## 2. Configuración de Red
Se configuraron tres segmentos en el router `Router_FW`:
* **LAN (G0/0):** 192.168.1.1/24.
* **DMZ (G0/1):** 192.168.2.1/24.
* **Internet (G0/2):** 192.168.3.1/24.

## 3. Implementación de NAT y Seguridad
* **NAT Estático:** Se mapeó la IP privada del servidor `192.168.2.10` a la IP pública `192.168.3.1` para permitir el acceso web externo.
* **ACL 101 (Entrada WAN):** Permite únicamente tráfico TCP por el puerto 80 (HTTP) hacia el servidor.
* **ACL 102 (Seguridad DMZ):** Deniega cualquier comunicación originada en la DMZ hacia la LAN interna, cumpliendo con el principio de seguridad de "confianza cero".

## 4. Resultados de las Pruebas
1. **Acceso Externo:** PC_External carga exitosamente la página web vía IP pública.
2. **Seguridad LAN:** El ping desde el servidor DMZ hacia la PC interna falla (Request Timeout) como se esperaba.
3. **Conectividad Interna:** PC_Internal accede correctamente al servidor DMZ.
