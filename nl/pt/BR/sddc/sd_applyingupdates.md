---

copyright:

  years:  2016, 2018

lastupdated: "2018-06-08"

---

{:tip: .tip}

# Aplicando atualizações a instâncias do Cloud Foundation

O console do {{site.data.keyword.vmwaresolutions_full}} periodicamente detecta e lista as atualizações de software disponíveis que podem ser aplicadas ao seu ambiente virtual do VMware.

Uma atualização disponível é um registro na lista de atualizações de software da instância, que pode ser aplicado imediatamente ou planejado para um horário posterior. A atualização é um pacote configurável que contém um ou mais pacotes para atualizar os componentes de gerenciamento da IBM e os componentes do VMware.

## Antes de iniciar

Antes de tentar aplicar uma atualização, expanda a entrada de atualização clicando na seta para baixo e verifique as informações a seguir:
* A versão da atualização. Deve-se aplicar as atualizações em sequência cronológica que é da mais antiga para a mais recente. Assegure-se de que tenha aplicado todas as atualizações anteriores antes de aplicar a mais recente. Por exemplo, deve-se aplicar a atualização V2.3 antes de tentar aplicar a atualização V2.4.
* Se o tempo de inatividade é necessário.
* O tempo estimado total para concluir a atualização.
* O impacto da atualização no ambiente virtual do VMware. A Tabela 1 mostra como os diferentes níveis de impacto afetam o sistema.
* Os detalhes da atualização.

Tabela 1. Atualize os níveis e o impacto

<table>
  <tr>
    <th>Atualizar nível</th>
    <th>Impacto</th>
  </tr>
  <tr>
    <td>Baixo</td>
    <td>Esta atualização não afeta nenhum sistema. Não é necessário aplicá-lo durante o tempo de inatividade planejado.</td>
  </tr>
  <tr>
    <td>Médio</td>
  <td>Esta atualização pode afetar alguns sistemas. Recomenda-se aplicar durante o tempo de inatividade planejado.</td>
  </tr>
    <tr>
    <td>Grave</td>
  <td>Esta atualização afeta alguns ou todos os sistemas. Deve-se aplicá-lo durante o tempo de inatividade planejado.</td>
  </tr>
</table>

## Procedimento

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Instâncias implementadas** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do Cloud Foundation**, clique na instância a ser atualizada.
3. Na página **Resumo**, verifique se todos os detalhes da instância são exibidos corretamente. Em seguida, clique em **Infraestrutura** na área de janela de navegação esquerda para verificar os detalhes na página **Infraestrutura**.
   Se os detalhes não forem exibidos, isso poderá indicar um problema de conectividade com a máquina virtual IBM CloudDriver, como resultado de uma regra de firewall ou de outro problema de rede. Resolva o problema antes de continuar com a próxima etapa, caso contrário, a atualização poderá falhar.
4. Clique em **Atualização e correção** na área de janela de navegação esquerda.
5. Clique na seta para baixo para expandir a atualização que você deseja aplicar e, em seguida, conclua uma das etapas a seguir:
   *  Para iniciar a atualização imediatamente, clique no ícone de menu overflow na coluna **Ações** da entrada de atualização e, em seguida, clique em **Atualizar agora**.
   *  Para planejar uma atualização futura, clique no ícone de menu overflow na coluna **Ações** da entrada de atualização e, em seguida, clique em **Planejar atualização**. Selecione a data, o horário e o fuso horário quando desejar que a atualização seja iniciada. Clique em **OK**.
6. Se você estiver aplicando atualizações a instâncias do Cloud Foundation na configuração de implementação de vários sites, uma seção intitulada **Etapas necessárias para a atualização** será exibida. Esta seção lista as operações de atualização necessárias para todas as instâncias na implementação de vários sites. Deve-se concluir as etapas em sequência clicando em **Aplicar atualização** para cada etapa. Deve-se aguardar a conclusão da etapa anterior antes de iniciar a próxima etapa.

## Resultados

1. Antes de uma operação de atualização ser iniciada, uma verificação de funcionamento da instância será concluída. Se a verificação de funcionamento falhar, você será notificado para que possa corrigir o problema antes de aplicar a atualização.
2. Antes de uma operação de atualização ser iniciada, um backup das máquinas virtuais (VMs) de gerenciamento será feito automaticamente, se sua instância tiver um serviço de backup instalado. Depois que o backup for concluído, a atualização será aplicada. Durante a operação de atualização, não tente nenhum fornecimento ou inclua operações do servidor ESXi.
3. Durante as atualizações que incluem atualizações de componentes do VMware, as VMs podem precisar ser migradas de servidores ESXi para entrarem no modo de manutenção. Se uma VM tiver um armazenamento de dados local ou CD-ROM montado, isso poderá impedir a migração da VM.
4. Durante o fornecimento de um novo ambiente, o {{site.data.keyword.vmwaresolutions_short}} cria o ID **automationuser** que é usado para gerenciamento da instância, incluindo para aplicar atualizações. Não mude a senha para esse ID do usuário. Mudar a senha pode fazer com que a atualização falhe.

5. Depois que uma atualização for aplicada, aparecerá um registro na lista de status de atualização de software, no qual é possível visualizar o progresso detalhado e o status da atualização. Quando a atualização for concluída com êxito, um registro aparecerá na lista de atualizações de softwares instalados.

  Para recuperar o status mais recente para uma tarefa de atualização, clique no ícone de atualização no canto superior direito da página.
  {:tip}

6. Para obter detalhes sobre os status de atualização, veja a tabela a seguir.

   Tabela 2: Detalhes de status de atualização

    <table>
      <tr>
        <th>Barra de Status</th>
        <th>Detalhes</th>
      </tr>
      <tr>
        <td>Disponível</td>
        <td>A atualização está disponível para ser aplicada. Não é possível selecionar uma atualização disponível até que todas as suas atualizações anteriores sejam aplicadas.</td>
      </tr>
      <tr>
        <td>Em andamento</td>
      <td>A tarefa de atualização foi iniciada, mas não foi concluída ainda. Não será possível aplicar nenhuma outra atualização até que a tarefa de atualização atual esteja concluída. </td>
      </tr>
        <tr>
        <td>Instalado</td>
      <td>A tarefa de atualização está concluída. O componente correspondente da plataforma VMware foi atualizado.</td>
      </tr>
        <tr>
        <td>Com falha</td>
      <td>A tarefa de atualização falha. O console relata um erro para a falha de atualização. Revise o erro e corrija o problema relatado antes de reaplicar a atualização.</td>
      </tr>
          <tr>
        <td>Planejado</td>
      <td>A tarefa de atualização está planejada para um momento posterior. A tarefa de atualização é iniciada automaticamente no momento planejado.</td>
      </tr>
          <tr>
        <td>Desconhecido</td>
      <td>O status da tarefa de atualização não pode ser obtido. Entre em contato com o Suporte IBM para obter assistência.</td>
      </tr>
    </table>

7. Se o processo de atualização falhar em uma etapa específica, [entre em contato com o Suporte IBM](../vmonic/trbl_support.html) para obter assistência. Você será avisado sobre como resolver o problema e será orientado a reiniciar o upgrade a partir da etapa que falhou.

## Links relacionados

* [Visão geral do Cloud Foundation](../sddc/sd_cloudfoundationoverview.html)
* [Veeam on IBM Cloud Visão Geral](../services/veeam_considerations.html)
* [Entrando em contato com o Suporte IBM](../vmonic/trbl_support.html)
* [Perguntas Mais Frequentes](../vmonic/faq.html)
