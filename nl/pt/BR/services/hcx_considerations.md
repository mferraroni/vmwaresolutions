---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-14"

---

# VMware HCX on IBM Cloud Visão Geral

O serviço HCX no {{site.data.keyword.cloud}} pode ampliar continuamente as redes de data centers no local para o {{site.data.keyword.cloud_notm}}, que permite que máquinas virtuais (VMs) sejam migradas para e do {{site.data.keyword.cloud_notm}} sem nenhuma conversão ou mudança.

**Disponibilidade**: esse serviço está disponível somente para instâncias do VMware vCenter Server on IBM Cloud with Hybridity Bundle que são implementadas na V2.3 e liberações mais recentes.

É possível fazer upgrade de sua instância do vCenter Server existente para uma instância do vCenter Server with Hybridity Bundle. Para obter mais informações sobre o upgrade de sua instância e a implementação do serviço HCX on {{site.data.keyword.cloud_notm}}, veja [Fazendo upgrade para a instância do vCenter Server with Hybridity Bundle](../vcenter/vc_applyingupdates.html#applying-updates-to-vcenter-server-instances.html#upgrading-to-the-vcenter-server-with-hybridity-bundle-instance).

**Nota:** uma instância do vCenter Server com o HCX no {{site.data.keyword.cloud_notm}} é limitada a três conexões simultâneas por meio de sites no local.

## Considerações ao instalar o HCX no IBM Cloud

Revise as considerações a seguir antes de tentar instalar o HCX no {{site.data.keyword.cloud_notm}}.

### Requisitos no número de servidores ESXi

O serviço HCX no {{site.data.keyword.cloud_notm}} não pode ser instalado em uma instância para a qual o cluster padrão tem mais de 51 servidores ESXi. Como o HCX no {{site.data.keyword.cloud_notm}} requer oito endereços IP na sub-rede do vMotion no cluster padrão, se o número de servidores ESXi exceder 51, nenhum endereço IP na sub-rede do vMotion estará disponível para o HCX no {{site.data.keyword.cloud_notm}}.

### Requisitos em regras de firewall

Antes de instalar o serviço HCX no {{site.data.keyword.cloud_notm}}, deve-se incluir uma regra de firewall em todos os firewalls existentes para permitir todo o tráfego HTTPS de saída para que o dispositivo virtual HCX Manager (HCX Manager) possa se registrar. Após a conclusão da instalação do HCX Manager, você poderá remover a regra de firewall. Além disso, deve-se configurar regras de firewall para permitir que o HCX funcione corretamente. Para obter mais informações, veja *Apêndice A - Requisitos de acesso de porta* em [Arquitetura do HCX on {{site.data.keyword.cloud_notm}}](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf).

## Considerações ao remover o HCX no IBM Cloud

Revise as considerações a seguir antes de remover o serviço HCX no {{site.data.keyword.cloud_notm}}:
* Assegure-se de que as interconexões e as redes estendidas entre o site de origem no local e os sites de destino do {{site.data.keyword.cloud_notm}} sejam removidas. Para remover as interconexões e as redes estendidas, use a interface com o usuário HCX no VMware vSphere Web Client no local.
* Assegure-se de que os pares de site entre o site de origem no local e os sites de destino do {{site.data.keyword.cloud_notm}} sejam removidos. Para remover os pares de site, use a interface com o usuário HCX no VMware vSphere Web Client no local.
* A remoção do HCX no {{site.data.keyword.cloud_notm}} é automatizada. Os procedimentos a seguir são concluídos para a remoção bem-sucedida desse serviço:
   * A licença HCX pedida para o gerenciador de HCX do lado da nuvem está desativada.
   * O gerenciador de HCX é excluído.
   * Os endereços IP do vMotion que foram reservados para o HCX são liberados.
   * Se vazios, os conjuntos de recursos relacionados ao HCX são removidos.
   * Se vazias, as pastas relacionadas ao HCX são removidas.
   * Os dispositivos de borda de gerenciamento do HCX são excluídos.

## Links relacionados

* [Solicitando HCX no {{site.data.keyword.cloud_notm}}](hcx_ordering.html)
* [Gerenciando o HCX no {{site.data.keyword.cloud_notm}}](managinghcx.html)
* [Glossário de termos do HCX](hcx_glossary.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
* [Visão geral do VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx)
* [Documentação do VMware Hybrid Cloud Extension](https://hcx.vmware.com/#vm-documentation)
