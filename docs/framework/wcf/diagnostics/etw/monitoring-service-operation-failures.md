---
title: "Monitorando operações de serviços com falha"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59472ba3-8ebf-4479-bd7b-f440d5e636cb
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ce62eb348cb57ce6137c58fbc50a32e829980c0c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="monitoring-service-operation-failures"></a>Monitorando operações de serviços com falha
Se o rastreamento analítico é habilitado para um aplicativo, falhas de serviço podem facilmente ser monitoradas no Visualizador de eventos.  Este tópico demonstra como determinar quando uma operação de serviço falha e como determinar o que causou a falha.  
  
### <a name="determining-service-operation-failure-information"></a>Determinando as informações de falha de operação de serviço  
  
1.  Abra o Visualizador de eventos clicando **iniciar**, **executar**e digitando `eventvwr.exe`.  
  
2.  Se você ainda não ativou o rastreamento analítico, expanda **Applications and Services Logs**, **Microsoft**, **Windows**, **aplicativos de servidor de aplicativo** . Selecione **exibição**, **Mostrar analítica e Logs de depuração**. Clique com botão direito **analítico** e selecione **Habilitar Log**. Visualizador de eventos deixe aberto para que os rastreamentos podem ser exibidos depois que a operação de serviço falhará.  
  
3.  Em seguida, abra o exemplo criado o [Tutorial de Introdução](../../../../../docs/framework/wcf/getting-started-tutorial.md) na [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] Observe que você deve executar [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] como um administrador para que o serviço pode ser criado. Se você tiver o [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] exemplos instalados, você pode abrir o [Introdução](../../../../../docs/framework/wcf/samples/getting-started-sample.md), que contém o projeto completo criado no tutorial.  
  
4.  No arquivo Program.cs no projeto de servidor, adicione a seguinte linha de código para o início do `Divide` método o `CalculatorService` classe:  
  
    ```  
    if (n2 == 0) throw new DivideByZeroException();  
    ```  
  
5.  No arquivo Program.cs no projeto cliente, altere o valor atribuído ao valor2 como zero:  
  
    ```  
    //Call the Divide service operation  
    value1 = 22.00D;  
    value2 = 0.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0}, {1}) = {2}", value1, value2, result);  
    ```  
  
6.  Execute o aplicativo de servidor sem depuração pressionando **Ctrl + F5**.  
  
7.  Abra um prompt de comando do Visual Studio.  Navegue até o diretório de cliente e executar o cliente de linha de comando.  
  
8.  No Visualizador de eventos, desabilitar e atualize o log analítico e classifique os eventos por ID do evento.  Procure um evento com ID de evento [ServiceException 219 -](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md), que descreve a falha do serviço.  
  
    ```Output  
    There was an unhandled exception of type 'System.DivideByZeroException' during message processing.  Full Exception ToString: System.DivideByZeroException: Attempted to divide by zero.  
    ```  
  
    > [!NOTE]
    >  Eventos são armazenados em buffer quando estão sendo enviados para o Visualizador de eventos; o evento de falha pode não aparecer imediatamente.
