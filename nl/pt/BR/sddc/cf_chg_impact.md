---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-08"

---

# Considerações sobre como alterar os artefatos do Cloud Foundation

Mudar usuários, recursos ou sub-redes que são reservados para o {{site.data.keyword.vmwaresolutions_full}} pode afetar as operações de gerenciamento para instâncias do VMware Cloud Foundation.

## As contas do usuário de serviço específico

Cada serviço cria uma conta de usuário interna no vCenter Server. Esta conta é necessária para que as operações de gerenciamento associadas a um serviço possam se conectar ao vCenter Server para executar as operações no serviço.

**Importante**: para evitar indisponibilidades e problemas de conexão, se você mudar as configurações de ID do usuário, senha ou expiração de senha para essa conta do usuário, assegure-se de também atualizar as informações no serviço associado.

O ID do usuário para esta conta está no formato `<service_name>-<service_uuid>@VSPHERE.LOCAL`. Por exemplo, o ID do usuário usado pelo serviço Veeam on {{site.data.keyword.cloud_notm}} para se conectar ao vCenter Server para executar backups planejados é `Veeam-<Veeam_uuid>@VSPHERE.LOCAL`.

## Recursos do VMware para instâncias do Cloud Foundation

A tabela a seguir lista as operações que poderão ser afetadas se você mudar os recursos do VMware fora do console do {{site.data.keyword.vmwaresolutions_short}}. Se uma solução para recuperar estiver disponível, ela também será fornecida.

Tabela 1. Operações que são afetadas para o administrador SSO (cliente)

| Mudança tentada  | Operações afetadas  | Severidade  | Método de recuperação  |
|:------------- |:------------- |:--------------|:--------------|
| Mude o nome do data center virtual do VMware. | A inclusão de um data center do VMware pode falhar porque o novo servidor ESXi não pode se associar ao data center mudado. | Importante | Mude o nome do data center virtual do VMware de volta para o nome original. |
| Mude quaisquer nomes do grupo da porta.    | A inclusão de um servidor ESXi pode falhar. | Importante | Mude o nome do grupo da porta de volta para o nome original. |
| Mude o nome do cluster. | A inclusão de um servidor ESXi pode falhar. | Importante | Mude o nome do cluster de volta para o nome original.
| Mude o nome do Comutador virtual distribuído (DVS) público ou privado. | A inclusão de um servidor ESXi pode falhar. | Importante | Mude o nome do DVS de volta para o nome original.
| Mude o nome do armazenamento de dados VSAN. | A inclusão de um servidor ESXi pode falhar.<br><br>Atualizando a instância poderá falhar. | Importante | Mude o nome do armazenamento de dados VSAN de volta para o nome original, **vsanDatastore**.
| Mude o nome da instância ou o nome de domínio. | A instância está inutilizável. | Crítico | N/A

## Gerenciamento de sub-redes para instâncias do Cloud Foundation

As informações a seguir discutem as sub-redes pedidas pelo {{site.data.keyword.vmwaresolutions_short}} e fornecem opções para você pedir sub-redes extras para seu próprio uso.

**CUIDADO**: não use esses componentes para outros propósitos ou a estabilidade de seu ambiente será seriamente comprometida.

Com cada pedido do Bare Metal Server do {{site.data.keyword.cloud_notm}}, os intervalos de endereços IP a seguir são pedidos por padrão:

*  Um intervalo público primário de 32 endereços IP
*  Um intervalo privado primário de 64 endereços IP

Além disso, as sub-redes de gerenciamento a seguir também são reservadas para o {{site.data.keyword.vmwaresolutions_short}}:

*  Duas sub-redes privadas móveis de 64 endereços IP na primeira VLAN: uma para gerenciamento e a outra para VTEPS.
*  Duas sub-redes privadas móveis de 64 endereços IP na segunda VLAN: uma para vMotion e uma para vSAN.
*  Uma sub-rede móvel pública de 16 endereços IP na VLAN pública.

Se precisar usar mais sub-redes, será possível obter endereços IP para usar em uma das maneiras a seguir:

* **Opção 1 (recomendado)**: use sobreposições de rede virtual VMware NSX. Um modelo VXLAN de amostra é fornecido quando pedido. Esse modelo VXLAN pode ser usado como um ponto de início para construir a SDN.
* **Opção 2**: peça suas próprias sub-redes móveis públicas ou privadas para obter endereços IP. Para distinguir as sub-redes pedidas das sub-redes de gerenciamento, é possível incluir notas em todas as sub-redes que estão sendo pedidas.
