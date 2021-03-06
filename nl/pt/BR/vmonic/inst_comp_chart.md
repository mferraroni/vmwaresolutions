---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-25"

---

# Gráfico de comparação Oferta

Revise o gráfico a seguir para entender as diferenças no suporte de funções para instâncias do VMware Cloud Foundation, instâncias do VMware vCenter Server, instâncias do VMware vCenter Server with Hybridity Bundle e clusters do VMware vSphere.

Tabela 1. Funções suportadas para os clusters do Cloud Foundation, vCenter Server, vCenter Server with Hybridity Bundle e vSphere

| Função                          | Cloud Foundation    | vCenter Server | VCenter Server with Hybridity | VMware vSphere |
|:----------------------------------|:--------------------|:---------------|:-------------------------|:-------------- |
| Desenvolvido por automação avançada {{site.data.keyword.IBM}} <sup>1</sup> | Sim | Sim | Sim | Não. Autoconstruído e configurado |
| Opções de armazenamento        | vSAN                | Armazenamento vSAN ou no nível de Arquivo compartilhado (NFS) | vSAN | Armazenamento vSAN ou no nível de Arquivo compartilhado (NFS) |
| Número de servidores ESXi no cluster inicial | 4 | 4 para vSAN e um mínimo de 2 (com 3 fortemente recomendado) para NFS | 4 | 1 para escalar um cluster existente, 4 para novo cluster vSAN e um mínimo de 3 para o novo cluster com NFS |
| Número máximo de servidores ESXi <sup>2</sup> | 32 por cluster      | 59 por cluster     | 59 por cluster | 60 por cluster     |
| Implementação de vários sites automatizada em nuvem | Suportado para novas instâncias implementadas na V2.0 ou mais recente | Suportado para novas instâncias implementadas na V2.0 ou mais recente | Suportado | Suportado. Configuração automatizada não incluída |
| Incluir servidores ESXi              | Suportado           | Suportado | Suportado | Suportado. Configuração automatizada não incluída |
| Remover servidores ESXi           | Suportado           | Suportado | Suportado | Suportado. Configuração automatizada não incluída |
| Suporte multi-cluster         | 5 clusters | 10 clusters | 10 clusters | Suportado. Configuração automatizada não incluída |
| Atualização e correção gerenciadas pelo cliente da pilha do VMware | Atualizações do IBM CloudDriver e do VMware | IBM CloudDriver | IBM CloudDriver |Correção automatizada não incluída |
| Backup e restauração            | Suportado | Suportado | Suportado | Configuração da solução de backup automatizada não incluída |
| Rede definida por software   | NSX Enterprise   | NSX Base, Advanced ou Enterprise | NSX Advanced ou Enterprise | NSX Standard, Base ou Enterprise. Configuração automatizada não incluída |
| BYOL para vSphere e vSAN | Totalmente suportado por cluster   | Totalmente suportado por cluster     | Não suportado | Suportado |
| BYOL para vCenter e NSX | Totalmente suportado por instância   | Totalmente suportado por instância     | Não suportado | Suportado |
| Opções de upgrade de licença NSX           | Nenhum   | Upgrade disponível do NSX Base para Advanced ou Enterprise e do NSX Advanced para Enterprise. O upgrade para o Pacote configurável vCenter Server with Hybridity está disponível. | Upgrade disponível do NSX Advanced para Enterprise  | Nenhum |
| Edições de licença do vSAN         | vSAN Advanced ou Enterprise  | vSAN Advanced ou Enterprise  | vSAN Advanced ou Enterprise | vSAN Advanced ou Enterprise  |
| Serviços de complemento               | Suportados, não incluindo o HCX no {{site.data.keyword.cloud_notm}}.  | Suportados, não incluindo o HCX no {{site.data.keyword.cloud_notm}}. O upgrade para o Pacote configurável vCenter Server with Hybridity está disponível. | Suportado, incluindo o HCX no {{site.data.keyword.cloud_notm}}. | Suportado. Configuração automatizada não incluída |

**Notas**:

<sup>1</sup> Segundo um design validado e com a verificação durante a implementação.

<sup>2</sup> É possível aumentar o número de servidores ESXi em um cluster vSAN para um máximo de 64. Para obter mais informações, consulte _Quantos servidores ESXi posso incluir em um cluster?_ em [Perguntas mais frequentes sobre servidores ESXi](faq_esxi.html).

### Links relacionados

* [Perguntas mais frequentes](faq.html)
* [Visão geral do Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Visão geral do vCenter Server](../vcenter/vc_vcenterserveroverview.html)
* [vCenter Server sua visão geral](../vcenter/vc_hybrid_overview.html)
* [Visão geral do Vmware vSphere](../vsphere/vs_vsphereclusteroverview.html)
* [BOM do Cloud Foundation](../sddc/sd_bom.html)
* [BOM do vCenter Server](../vcenter/vc_bom.html)
* [BOM do Vmware vSphere](../vsphere/vs_bom.html)
