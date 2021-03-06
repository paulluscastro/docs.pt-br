---
title: Como criar um participante de rastreamento personalizado
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d53035c2fb41800a91d3cdea134ae811a09fa3e9
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-create-a-custom-tracking-participant"></a>Como criar um participante de rastreamento personalizado
O rastreamento de fluxo de trabalho fornece a visibilidade ao status da execução do fluxo de trabalho. O tempo de execução do fluxo de trabalho emite os registros de rastreamento que descrevem os eventos de ciclo de vida do fluxo de trabalho, os eventos de ciclo de vida da atividade, os reinícios do indicador e as falhas. Esses registros de rastreamento são consumidos pelos participantes. Windows Workflow Foundation (WF) inclui um participante de rastreamento padrão que grava os registros de rastreamento como eventos de rastreamento de eventos para Windows (ETW). Se isso não atender aos requisitos, você também poderá escrever um participante de rastreamento personalizado. Esta etapa do tutorial descreve como criar um participante de rastreamento personalizado e um perfil de rastreamento que captura a saída das atividades `WriteLine` de forma que elas possam ser exibidas para o usuário.  
  
> [!NOTE]
>  Cada tópico do tutorial de Introdução depende dos tópicos anteriores. Para concluir este tópico, primeiro você deve concluir os tópicos anteriores. Para baixar a versão completa ou exibir um vídeo passo a passo do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="in-this-topic"></a>Neste tópico  
  
-   [Para criar o participante de rastreamento personalizado](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_CustomTrackingParticipant)  
  
-   [Para criar o perfil de rastreamento e registrar o participante de rastreamento](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile)  
  
-   [Para exibir as informações de rastreamento](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_DisplayTracking)  
  
-   [Para compilar e executar o aplicativo](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_BuildAndRun)  
  
###  <a name="BKMK_CustomTrackingParticipant"></a> Para criar o participante de rastreamento personalizado  
  
1.  Clique com botão direito **NumberGuessWorkflowHost** na **Solution Explorer** e escolha **adicionar**, **classe**. Tipo `StatusTrackingParticipant` para o **nome** caixa e clique em **adicionar**.  
  
2.  Adicione as seguintes instruções `using` (ou `Imports`) na parte superior do arquivo com as outras instruções `using` (ou `Imports`).  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3.  Modifique a classe `StatusTrackingParticipant` de forma que ela herde de `TrackingParticipant`.  
  
    ```vb  
    Public Class StatusTrackingParticipant  
        Inherits TrackingParticipant  
  
    End Class  
    ```  
  
    ```csharp  
    class StatusTrackingParticipant : TrackingParticipant  
    {  
    }  
    ```  
  
4.  Adicione a substituição do método de `Track` a seguir. Há vários tipos diferentes de registros de rastreamento. Estamos interessados na saída das atividades de `WriteLine`, que estão contidas nos registros de rastreamento da atividade. Se o `TrackingRecord` for um `ActivityTrackingRecord` para uma atividade `WriteLine`, o `Text` de `WriteLine` será acrescentado a um arquivo com o nome da `InstanceId` do fluxo de trabalho. Neste tutorial, o arquivo é salvo na pasta atual do aplicativo host.  
  
    ```vb  
    Protected Overrides Sub Track(record As TrackingRecord, timeout As TimeSpan)  
        Dim asr As ActivityStateRecord = TryCast(record, ActivityStateRecord)  
  
        If Not asr Is Nothing Then  
            If asr.State = ActivityStates.Executing And _  
            asr.Activity.TypeName = "System.Activities.Statements.WriteLine" Then  
  
                'Append the WriteLine output to the tracking  
                'file for this instance.  
                Using writer As StreamWriter = File.AppendText(record.InstanceId.ToString())  
                    writer.WriteLine(asr.Arguments("Text"))  
                    writer.Close()  
                End Using  
            End If  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    protected override void Track(TrackingRecord record, TimeSpan timeout)  
    {  
        ActivityStateRecord asr = record as ActivityStateRecord;  
  
        if (asr != null)  
        {  
            if (asr.State == ActivityStates.Executing &&  
                asr.Activity.TypeName == "System.Activities.Statements.WriteLine")  
            {  
                // Append the WriteLine output to the tracking  
                // file for this instance  
                using (StreamWriter writer = File.AppendText(record.InstanceId.ToString()))  
                {  
                    writer.WriteLine(asr.Arguments["Text"]);  
                    writer.Close();  
                }  
            }  
        }  
    }  
    ```  
  
     Quando nenhum perfil de rastreamento for especificado, o perfil padrão de rastreamento será usado. Quando o perfil padrão do rastreamento for usado, os registros de rastreamento serão emitidos para todos os `ActivityStates`. Como somente precisamos capturar o texto uma vez durante o ciclo de vida da atividade `WriteLine`, somente extraímos o texto do estado `ActivityStates.Executing`. Em [para criar o perfil de rastreamento e registrar o participante de rastreamento](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile), será criado um perfil de rastreamento que especifica que somente `WriteLine` `ActivityStates.Executing` registros de rastreamento são emitidos.  
  
###  <a name="BKMK_TrackingProfile"></a> Para criar o perfil de rastreamento e registrar o participante de rastreamento  
  
1.  Clique com botão direito **WorkflowHostForm** na **Solution Explorer** e escolha **Exibir código**.  
  
2.  Adicione a seguinte instrução `using` (ou `Imports`) na parte superior do arquivo com as outras instruções `using` (ou `Imports`).  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3.  Adicione o seguinte código ao `ConfigureWorkflowApplication` depois do código que adiciona o `StringWriter` às extensões de fluxo de trabalho e antes dos manipuladores de ciclo de vida de fluxo de trabalho.  
  
    ```vb  
    'Add the custom tracking participant with a tracking profile  
    'that only emits tracking records for WriteLine activities.  
    Dim query As New ActivityStateQuery()  
    query.ActivityName = "WriteLine"  
    query.States.Add(ActivityStates.Executing)  
    query.Arguments.Add("Text")  
  
    Dim profile As New TrackingProfile()  
    profile.Queries.Add(query)  
  
    Dim stp As New StatusTrackingParticipant()  
    stp.TrackingProfile = profile  
  
    wfApp.Extensions.Add(stp)  
    ```  
  
    ```csharp  
    // Add the custom tracking participant with a tracking profile  
    // that only emits tracking records for WriteLine activities.  
    StatusTrackingParticipant stp = new StatusTrackingParticipant  
    {  
        TrackingProfile = new TrackingProfile  
        {  
            Queries =   
            {  
                new ActivityStateQuery  
                {  
                    ActivityName = "WriteLine",  
                    States = { ActivityStates.Executing },  
                    Arguments = { "Text" }  
                }  
            }  
        }  
    };  
  
    wfApp.Extensions.Add(stp);  
    ```  
  
     Este perfil de rastreamento especifica que somente os registros de estado de atividade para atividades `WriteLine` no estado `Executing` são emitidos para o participante de rastreamento personalizado.  
  
     Depois de adicionar o código, o início de `ConfigureWorkflowApplication` se parecerá com o exemplo a seguir.  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
        'Configure the persistence store.  
        wfApp.InstanceStore = store  
  
        'Add a StringWriter to the extensions. This captures the output  
        'from the WriteLine activities so we can display it in the form.  
        Dim sw As New StringWriter()  
        wfApp.Extensions.Add(sw)  
  
        'Add the custom tracking participant with a tracking profile  
        'that only emits tracking records for WriteLine activities.  
        Dim query As New ActivityStateQuery()  
        query.ActivityName = "WriteLine"  
        query.States.Add(ActivityStates.Executing)  
        query.Arguments.Add("Text")  
  
        Dim profile As New TrackingProfile()  
        profile.Queries.Add(query)  
  
        Dim stp As New StatusTrackingParticipant()  
        stp.TrackingProfile = profile  
  
        wfApp.Extensions.Add(stp)  
  
        'Workflow lifecycle handlers...  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {  
        // Configure the persistence store.  
        wfApp.InstanceStore = store;  
  
        // Add a StringWriter to the extensions. This captures the output  
        // from the WriteLine activities so we can display it in the form.  
        StringWriter sw = new StringWriter();  
        wfApp.Extensions.Add(sw);  
  
        // Add the custom tracking participant with a tracking profile  
        // that only emits tracking records for WriteLine activities.  
        StatusTrackingParticipant stp = new StatusTrackingParticipant  
        {  
            TrackingProfile = new TrackingProfile  
            {  
                Queries =   
                {  
                    new ActivityStateQuery  
                    {  
                        ActivityName = "WriteLine",  
                        States = { ActivityStates.Executing },  
                        Arguments = { "Text" }  
                    }  
                }  
            }  
        };  
  
        wfApp.Extensions.Add(stp);  
  
        // Workflow lifecycle handlers...  
    ```  
  
###  <a name="BKMK_DisplayTracking"></a> Para exibir as informações de rastreamento  
  
1.  Clique com botão direito **WorkflowHostForm** na **Solution Explorer** e escolha **Exibir código**.  
  
2.  No manipulador `InstanceId_SelectedIndexChanged`, adicione o seguinte código imediatamente depois do código que limpa a janela de status.  
  
    ```vb  
    'If there is tracking data for this workflow, display it  
    'in the status window.  
    If File.Exists(WorkflowInstanceId.ToString()) Then  
        Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
        UpdateStatus(status)  
    End If  
    ```  
  
    ```csharp  
    // If there is tracking data for this workflow, display it  
    // in the status window.  
    if (File.Exists(WorkflowInstanceId.ToString()))  
    {  
        string status = File.ReadAllText(WorkflowInstanceId.ToString());  
        UpdateStatus(status);  
    }  
    ```  
  
     Quando um novo fluxo de trabalho é selecionado na lista de fluxo de trabalho, os registros de rastreamento para esse fluxo de trabalho são carregados e exibidos na janela de status. O exemplo a seguir é o manipulador `InstanceId_SelectedIndexChanged` concluído.  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
        If InstanceId.SelectedIndex = -1 Then  
            Return  
        End If  
  
        'Clear the status window.  
        WorkflowStatus.Clear()  
  
        'If there is tracking data for this workflow, display it  
        'in the status window.  
        If File.Exists(WorkflowInstanceId.ToString()) Then  
            Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
            UpdateStatus(status)  
        End If  
  
        'Get the workflow version and display it.  
        'If the workflow is just starting then this info will not  
        'be available in the persistence store so do not try and retrieve it.  
        If Not WorkflowStarting Then  
            Dim instance As WorkflowApplicationInstance = _  
                WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
            WorkflowVersion.Text = _  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)  
  
            'Unload the instance.  
            instance.Abandon()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
        if (InstanceId.SelectedIndex == -1)  
        {  
            return;  
        }  
  
        // Clear the status window.  
        WorkflowStatus.Clear();  
  
        // If there is tracking data for this workflow, display it  
        // in the status window.  
        if (File.Exists(WorkflowInstanceId.ToString()))  
        {  
            string status = File.ReadAllText(WorkflowInstanceId.ToString());  
            UpdateStatus(status);  
        }  
  
        // Get the workflow version and display it.  
        // If the workflow is just starting then this info will not  
        // be available in the persistence store so do not try and retrieve it.  
        if (!WorkflowStarting)  
        {  
            WorkflowApplicationInstance instance =  
                WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);  
  
            WorkflowVersion.Text =  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);  
  
            // Unload the instance.  
            instance.Abandon();  
        }  
    }  
    ```  
  
###  <a name="BKMK_BuildAndRun"></a> Para compilar e executar o aplicativo  
  
1.  Pressione Ctrl+Shift+B para criar o aplicativo.  
  
2.  Pressione Ctrl+F5 para iniciar o aplicativo.  
  
3.  Selecione um intervalo para o jogo de adivinhação Pro e o tipo de fluxo de trabalho para iniciar e, em seguida, clique em **novo jogo**. Insira uma estimativa no **estimativa** caixa e clique em **vá** para enviar sua estimativa. Observe que o status do fluxo de trabalho é exibido na janela de status. Essa saída é capturada das atividades `WriteLine`. Alternar para um fluxo de trabalho diferente, selecione um no **Id de instância de fluxo de trabalho** caixa de combinação e observe que o status do fluxo de trabalho atual é removido. Alterne novamente para o fluxo de trabalho e observe que o status é restaurado, semelhante ao exemplo a seguir.  
  
    > [!NOTE]
    >  Se você alternar para um fluxo de trabalho que foi iniciado antes que o rastreamento foi habilitado, nenhum status será exibido. No entanto, se você fizer previsões adicionais, seu status será salvo porque o rastreamento agora estará habilitado.  
  
 **Insira um número entre 1 e 10**  
**Sua estimativa é muito alta.**   
**Insira um número entre 1 e 10**    
    > [!NOTE]
    >  Essas informações são úteis para determinar o intervalo do número aleatório, mas ele não contém informações sobre os palpites que já foram feitos anteriormente. Essas informações estão na próxima etapa, [como: Host várias versões de uma fluxo de trabalho lado a lado](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).  
  
     Faça uma anotação da ID de instância de fluxo de trabalho e jogue até o final.  
  
4.  Abra o Windows Explorer e navegue até o **NumberGuessWorkflowHost\bin\debug** pasta (ou **bin\release** dependendo de suas configurações de projeto). Observe que, além dos arquivos executáveis de projeto, há arquivos com nomes de arquivo de GUID. Identifique o que corresponde à ID da instância do fluxo de trabalho concluído na etapa anterior e abra-o no Bloco De Notas. As informações de rastreamento contêm informações semelhantes ao seguinte.  
  
 **Insira um número entre 1 e 10**  
**Sua estimativa é muito alta.**   
**Insira um número entre 1 e 10**   
**Sua estimativa é muito alta.**   
**Insira um número entre 1 e 10** além de ausência de tentativas do usuário, dados de controle não contém informações sobre a previsão final do fluxo de trabalho. Isso ocorre porque as informações de rastreamento consistem apenas na saída de `WriteLine` do fluxo de trabalho, e a mensagem final que é exibida é feita a partir do manipulador `Completed` depois que o fluxo de trabalho é concluído. Na próxima etapa do tutorial, [como: Host várias versões de uma fluxo de trabalho lado a lado](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), existente `WriteLine` atividades são modificadas para exibir as previsões do usuário e adicional `WriteLine` atividade é adicionada que Exibe os resultados finais. Depois que essas alterações são integradas, [como: Host várias versões de uma fluxo de trabalho lado a lado](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) demonstra como hospedar várias versões de um fluxo de trabalho ao mesmo tempo.
