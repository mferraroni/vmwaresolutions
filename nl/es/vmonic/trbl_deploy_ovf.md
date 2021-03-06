---

copyright:

  years:  2016, 2018

lastupdated: "2018-03-16"

---

# Despliegue de un archivo OVF utilizando el cliente web de VMware vSphere

## Solución

Para desplegar un archivo OVF (Open Virtualization Format) utilizando el cliente web de vSphere, siga el procedimiento siguiente:
1. Antes de intentar el despliegue, debe añadir la siguiente información de host al archivo `/etc/hosts`:

   * Información de host para Platform Services Controller (PSC)
   * Información de host para el servidor VMware ESXi
   * Información de host para vCenter
2. Compruebe el archivo `/etc/hosts` para asegurarse de que esta información se ha añadido correctamente. Un ejemplo de archivo de host se parecería a la siguiente lista:

    ```javascript
    10.131.9.201  psc-myinstance.myinstance.mydomain.com
    10.131.7.26   host0.myinstance.mydomain.com
    10.131.7.39   host1.myinstance.mydomain.com
    10.131.7.6    host2.myinstance.mydomain.com
    10.131.7.48   host3.myinstance.mydomain.com
    10.131.9.196  vcenter-1.myinstance.mydomain.com
    ```
3. Asegúrese de que tiene acceso a todas las VPN (redes privadas virtuales) necesarias en el {{site.data.keyword.slportal_full}}. En este ejemplo, serían `10.131.7.xx` y `10.131.9.xxx`.
4. Registre la VPN en su centro de datos.
5. Pulse **vCenter** para acceder al cliente web de vSphere.
6. Pulse con el botón derecho del ratón en un host y despliegue un archivo `.ovf`.
