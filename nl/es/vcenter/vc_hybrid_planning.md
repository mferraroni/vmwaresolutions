---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-22"

---

# Requisitos y planificación de instancias de vCenter Server con el paquete híbrido (Hybridity)

Revise los siguientes requisitos antes de solicitar su instancia de VMware vCenter Server on {{site.data.keyword.cloud}} con el paquete híbrido (Hybridity). Planifique la instancia en función de la ubicación del {{site.data.keyword.CloudDataCent_notm}}, de sus requisitos de capacidad de carga de trabajo y de los requisitos de servicios adicionales.

## Requisitos de la cuenta de IBM Cloud

La cuenta de {{site.data.keyword.cloud_notm}} que utilice debe cumplir ciertos requisitos. Para obtener más información, consulte [Requisitos para la cuenta de {{site.data.keyword.cloud_notm}}](../vmonic/slaccountrequirement.html).

## Disponibilidad del centro de datos de IBM Cloud

El despliegue de vCenter Server con el paquete híbrido (Hybridity) impone requisitos estrictos en cuanto a la infraestructura física. Por lo tanto, en {{site.data.keyword.CloudDataCents_notm}} solo puede desplegar instancias que cumplan los requisitos. Están disponibles los siguientes {{site.data.keyword.CloudDataCents_notm}} para el despliegue de vCenter Server con el paquete híbrido (Hybridity):

Tabla 1. Disponible {{site.data.keyword.CloudDataCents_notm}} para instancias de vCenter Server con el paquete híbrido (Hybridity)

| Centro de datos de IBM Cloud | Ubicación | Región |
|:-----|:----------------|
| AMS03 | Amsterdam | Europa |
| CHE01 | Chennai | Asia-Pacífico |
| DAL09 | Dallas | América del Norte sur |
| DAL10 | Dallas | América del Norte sur |
| DAL12 | Dallas | América del Norte sur |
| DAL13 | Dallas | América del Norte sur |
| FRA02 | Frankfurt | Europa |
| FRA04 | Frankfurt | Europa |
| HKG02 | Hong Kong | Asia-Pacífico |
| LON02 | Londres | Europa |
| LON04 | Londres | Europa |
| LON06 | Londres | Europa |
| MEL01 | Melbourne | Asia-Pacífico |
| MEX01 | Queretaro | América del Norte sur |
| MIL01 | Milán | Europa |
| MON01 | Montreal | América del Norte este |
| OSL01 | Oslo | Europa |
| PAR01 | París | Europa |
| SAO01 | Sao Paulo | América del Sur |
| SEO01 | Seúl | Asia-Pacífico |
| SJC03 | San José | América del Norte oeste |
| SJC04 | San José | América del Norte oeste |
| SNG01 | Singapur | Asia-Pacífico |
| SYD01 | Sídney | Asia-Pacífico |
| SYD04 | Sídney | Asia-Pacífico |
| TOK02 | Tokio | Asia-Pacífico |
| TOR01 | Toronto | América del Norte este |
| WDC04 | Washington, DC | América del Norte este |
| WDC06 | Washington, DC | América del Norte este |
| WDC07 | Washington, DC | América del Norte este |

En función de la disponibilidad y del suministro de inventario, {{site.data.keyword.CloudDataCents_notm}} puede mostrar un indicador de estado en la consola de {{site.data.keyword.vmwaresolutions_full}} que le ayudará a planificar sus despliegues.

Tabla 2. Indicadores de estado para {{site.data.keyword.CloudDataCents_notm}} cuando se solicitan instancias de vCenter Server con el paquete híbrido (Hybridity)

| Estado | Detalles del estado |
|:------------------------------|:--------------------------------------------------|
| Coming Soon                   | El {{site.data.keyword.CloudDataCent_notm}} no está disponible actualmente. |
| Temporarily Out of Inventory  | El {{site.data.keyword.CloudDataCent_notm}} no ofrece disponibilidad en este momento. |
| Limited Inventory             | El {{site.data.keyword.CloudDataCent_notm}} ofrece disponibilidad limitada y es posible que el pedido no se complete. |

## Servicios para instancias de vCenter Server con el paquete híbrido (Hybridity)

La instancia de vCenter Server con el paquete híbrido (Hybridity) incluye la licencia de VMware Hybrid Cloud Extension (HCX) que le autoriza al servicio de VMware HCX on IBM Cloud. Este servicio permite ampliar fácilmente las redes de centros de datos locales en {{site.data.keyword.cloud_notm}}, lo que permite migrar las máquinas virtuales (VM) de {{site.data.keyword.cloud_notm}} y al mismo sin realizar ninguna conversión ni cambio.

Al desplegar este servicio, siga los valores siguientes:
* Especifique el **Tipo de interconexión de HCX** seleccionando una de las opciones siguientes:
  * **Red pública**: HCX crea una conexión cifrada entre sitios de la red pública.
  * **Red privada**: HCX crea una conexión cifrada entre sitios de la red privada.
* Especifique el **Tipo de certificado de punto final público**. Si selecciona **Certificado de CA**, configure los valores siguientes:
  * **Contenido del certificado**: especifique el contenido del certificado de CA.
  * **Clave privada**: especifique la clave privada del certificado de CA.
  * (Opcional) **Contraseña**: especifique la contraseña para la clave privada si está cifrada.
  * (Opcional) **Vuelva a escribir la contraseña**: vuelva a escribir la contraseña para la clave privada.
  * (Opcional) **Nombre de host**: especifique el nombre de host que se correlacionará con el nombre común (CN) del certificado de CA. HCX on {{site.data.keyword.cloud_notm}} requiere que el certificado de CA esté en un formato aceptado por NSX Edge. Para obtener más información sobre los formatos de certificado NSX Edge, consulte [Importación de certificados SSL](https://docs.vmware.com/en/VMware-NSX-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html).

Puede solicitar otros servicios complementarios para su instancia en función de sus necesidades, por ejemplo, la recuperación tras desastre. Para obtener más información, consulte [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_addingremovingservices.html).

## Enlaces relacionados

* [Visión general de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_overview.html)
* [Solicitud de instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_orderinginstance.html)
* [Ampliación y reducción de la capacidad para instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_addingremovingservers.html)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server con el paquete híbrido (Hybridity)](vc_hybrid_addingremovingservices.html)
