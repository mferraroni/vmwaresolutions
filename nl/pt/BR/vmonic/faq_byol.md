---

copyright:

  years:  2016, 2018

lastupdated: "2018-05-25"

---

# Perguntas mais frequentes sobre licenciamento e BYOL

Encontre respostas às perguntas mais frequentes sobre licenciamento, incluindo o recurso Bring Your Own License (BYOL) do {{site.data.keyword.vmwaresolutions_full}}.

## O que é BYOL?

Bring Your Own License, ou BYOL, é um recurso disponível para instâncias do VMware Cloud Foundation na V1.8 e liberações mais recentes e para clusters do vCenter Server e vSphere na V2.0 e liberações mais recentes. O BYOL permite usar as suas próprias licenças do VMware para um ou mais dos seguintes componentes do software do VMware ao pedir instâncias:
* VMware vCenter Server
* VMware vSphere
* VMware NSX
* VMware vSAN

Se você selecionar para usar sua própria licença para um componente do VMware e fornecer uma chave de licença válida para ele, nenhuma licença será pedida da IBM para esse componente e nenhum encargo mensal de licença será incorrido para sua conta de infraestrutura do {{site.data.keyword.cloud}} para esse componente.

**Nota:** o recurso BYOL não está disponível para usuários de Parceiro de Negócios.

## Onde gerencio as licenças e componentes pedidos por meio do VMware vSphere on IBM Cloud?

Após um pedido para criar um novo cluster para o VMware vSphere on {{site.data.keyword.cloud_notm}} ser feito, as licenças do VMware, os servidores ESXi e outros componentes de rede são fornecidos e podem ser gerenciados no {{site.data.keyword.slportal}}.

Após a implementação, acesse o console do {{site.data.keyword.vmwaresolutions_short}} para escalar o novo cluster usando a configuração salva. Para obter mais informações sobre ajuste de escala, veja [Ajustando a escala dos clusters do vSphere existentes](../vsphere/vs_scalingexistingclusters.html).

## Quais edições de licença e quantidades de CPU são necessárias para BYOL?

Os requisitos a seguir se aplicam às edições de licença para BYOL.

### Requisitos do BYOL para instâncias do vCenter Server

Tabela 1. Edições de licença e requisitos mínimos de CPU para instâncias do vCenter Server

  | Componente do VMware | Edição de licença necessária | Mínimo de CPU necessário
  |:-------------  |:-------------  |:-------|
  | vCenter Server | Padrão                | N/A |
  | vSphere        | Corporativo Plus | 8 CPUs |
  | vSAN           | Advanced ou Enterprise | 8 CPUs |
  | NSX            | Standard, Advanced ou Enterprise | 8 CPUs |

### Requisitos do BYOL para instâncias do Cloud Foundation

Tabela 2. Edições de licença e requisitos mínimos de CPU para instâncias do Cloud Foundation

  | Componente do VMware | Edição de licença necessária | Mínimo de CPU necessário
  |:-------------  |:-------------  |:-------|
  | vCenter Server | Padrão | N/A |
  | vSphere        | Corporativo Plus | 8 CPUs |
  | vSAN           | Advanced ou Enterprise | 8 CPUs |
  | NSX            | Corporativo | 8 CPUs |

## O que acontece se a chave de licença que eu forneci não estiver correta?

Todas as chaves de licença que você fornece são validadas para assegurar que estejam corretas para os componentes do VMware correspondentes e que atendam aos requisitos mínimos de edição e CPU dos componentes do VMware. Se a validação de qualquer chave de licença falhar, você receberá uma notificação e não poderá continuar com o pedido da instância.

## Posso fornecer uma chave de licença com mais de 8 CPUs?

Sim. Para cada componente do VMware, uma licença por CPU é necessária. Atualmente, todos os servidores vCenter Server e Cloud Foundation têm duas CPUs, portanto, são necessárias duas licenças para cada servidor. Recomenda-se que você forneça uma chave de licença que possa suportar a instância base e todos os nós de expansão que deseja incluir na instância no futuro.

## Posso fornecer a licença do SDDC Manager ao usar o recurso BYOL?

Não. Nosso contrato com o VMware exige que devemos aceitar uma chave de licença real de um cliente. Embora a implementação do Cloud Foundation inclua licenças do SDDC Manager, não há nenhum arquivo de chave de licença do SDDC Manager que possamos aceitar e validar para o BYOL. Portanto, as licenças do SDDC Manager são cobradas pela IBM para todas as instâncias. As licenças do SDDC Manager representam uma parte muito pequena dos encargos gerais de licenças para uma instância do Cloud Foundation.

## Posso usar o recurso BYOL para alguns componentes do VMware e comprar licenças mensais para outros?

Sim. É possível usar o recurso BYOL ou comprar licenças para qualquer combinação dos quatro componentes do VMware. O console do {{site.data.keyword.vmwaresolutions_short}} torna mais fácil para você selecionar a opção de licenciamento quando você pede a instância do vCenter Server ou Cloud Foundation. Sua opção de licenciamento no momento do pedido da instância inicial se aplica durante o tempo de vida dessa instância.

## Para um componente específico do VMware, posso usar o BYOL para algumas licenças e comprar o resto das licenças da IBM?

Sim. Se selecionou o BYOL para um componente específico do VMware, você tem a opção, ao criar um novo cluster para inserir uma nova chave do BYOL, de continuar usando a chave existente do BYOL ou comprar a licença fornecida pela IBM para esse cluster.  Nesse momento, apenas o VMware vSphere Enterprise e o VMware vSAN estão disponíveis para licenciamento por cluster.

## Posso usar o BYOL ao criar um novo cluster?

Sim. É possível usar o BYOL de licenças existentes do BYOL ou inserir um novo BYOL ao criar um novo cluster. Você também terá a opção de comprar uma licença de assinatura fornecida pela IBM ao criar um novo cluster. Neste momento, apenas o VMware vSphere Enterprise e o VMware vSAN estão disponíveis para licenciamento por cluster.

## Como posso gerenciar minhas licenças do BYOL?

É possível gerenciar suas licenças do BYOL usando o VMware vSphere Web Client após a implementação da instância ser concluída.

## Quando eu incluo mais servidores ESXi em minha instância posteriormente, a instância valida se a capacidade de minhas licenças do BYOL é suficiente?

Sim. Quando você está incluindo mais servidores ESXi em uma instância implementada, a capacidade de suas licenças do BYOL é automaticamente verificada quanto ao número especificado de servidores ESXi. Se a capacidade não for suficiente, os servidores ESXi não serão incluídos e você receberá uma notificação do console.

## Como posso dizer o quanto eu tenho de capacidade de licença disponível em um cluster com o BYOL?

É possível localizar o número de CPUs disponíveis em sua chave de licença acessando a página **Instâncias implementadas**, localizando e clicando na instância e, em seguida, na guia **Infraestrutura**, clicando no cluster para o qual você deseja verificar a capacidade de licença. O número de CPUs disponíveis é listado na tabela **Licença Fornecida pelo Usuário**.

## A IBM fornecerá suporte se eu selecionar a opção de licenciamento do BYOL?

O Suporte IBM continua sendo seu ponto de contato para qualquer questão de configuração da instância. No entanto, se o problema relatado for determinado como sendo de um componente do VMware do BYOL, você será direcionado para o Suporte do VMware.

## Por que os encargos de licença do vSphere aparecem na lista de estimativa de preço se eu estiver usando o BYOL? Estou sendo cobrado por isso?

Os {{site.data.keyword.baremetal_short}} são fornecidos com o VMware vSphere já instalado e com as licenças do vSphere já incluídas. Se você selecionou o BYOL para vSphere, um processo será automaticamente iniciado após a implementação da instância para remover as licenças incluídas do vSphere. Em seguida, os encargos de licença serão creditados à sua conta do {{site.data.keyword.cloud_notm}}. Você não tem que fazer nada neste processo.

## Ainda posso usar o processo manual existente para o BYOL?

Com a introdução do recurso BYOL, o uso contínuo do processo manual não é recomendado. Se desejar usar o BYOL, forneça suas próprias licenças quando estiver pedindo a instância.

## O BYOL é suportado para outros produtos do VMware, como VMware vRealize Automation, VMware vRealize Operations ou VMware vRealize Log Insight?

Não, porque esses produtos do VMware não fazem parte da implementação da instância. Esses produtos do VMware podem ser instalados no topo da implementação inicial, que requer que os clientes ou seus agentes executem a instalação e o licenciamento.

## Posso pedir armazenamento NFS com o vCenter Server with Hybridity Bundle?

Para instâncias implementadas recentemente, somente armazenamento totalmente em flash do vSAN é suportado. A oferta do vCenter Server with Hybridity Bundle inclui o licenciamento do vSAN Advanced ou Enterprise.

Se você tiver uma instância do vCenter Server com armazenamento NFS, será possível fazer upgrade de sua instância existente para o vCenter Server with Hybridity Bundle. Embora o licenciamento do vSAN Advanced seja pedido durante o upgrade, não é necessário provisionar um cluster do vSAN totalmente em flash.

## Posso usar o BYOL com o vCenter Server with Hybridity Bundle?

Não é possível usar bring your own licensing (BYOL) do VMware para o {{site.data.keyword.cloud_notm}}. O VCenter Server with Hybridity Bundle requer que todas as licenças do VMware sejam fornecidas pela IBM.

## Qual é a diferença entre o licenciamento do vCenter Server with Hybridity Bundle e o licenciamento do vCenter Server?

As licenças individuais do VMware que estão disponíveis no vCenter Server são precificadas por CPU. Como com todas as licenças do VMware por CPU fornecidas pela IBM, há um aumento de 1,3x no preço entre todos os servidores que possuem mais de 16 núcleos por CPU, por exemplo, para Dual Intel Xeon Gold 6140.

O vCenter Server with Hybridity Bundle é um conjunto prescrito de licenças e edições do VMware que são licenciadas por núcleo e não por CPU. Portanto, o preço de licenciamento para essas instâncias não muda.

## Quais componentes e edições de licença do VMware fornecidos pela IBM estão disponíveis para o vCenter Server with Hybridity Bundle?

Novas instâncias do vCenter Server with Hybridity Bundle incluem o VMware vSphere Enterprise Plus, VMware vCenter Standard, VMware NSX Advanced ou Enterprise, VMware vSAN Advanced ou Enterprise e VMware Hybrid Cloud Extension (HCX).

Se você tiver uma instância do vCenter Server com a edição NSX Base, será feito upgrade para o NSX Advanced automaticamente ao pedir o vCenter Server with Hybridity Bundle.

## Posso fazer upgrade da edição NSX Advanced que está incluída no vCenter Server with Hybridity Bundle para a edição NSX Enterprise?

Embora o vCenter Server with Hybridity Bundle inclua o NSX Advanced, é possível fazer upgrade para a edição NSX Enterprise depois de pedir o vCenter Server with Hybridity Bundle. Para fazer isso, use a guia **Atualização e correção** na guia da página de detalhes da instância do console do {{site.data.keyword.vmwaresolutions_short}}.

### Links relacionados

* [Pedindo instâncias do Cloud Foundation](../sddc/sd_orderinginstance.html)
* [Instâncias do Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Acessando o console](loginmethod.html)
* [Entrando em contato com o Suporte IBM](trbl_support.html)
* [vRealize Automation](https://www.ibm.com/devops/method/content/architecture/virtCloudFoundationPlatform/vRealizeAutomation){:new_window}
