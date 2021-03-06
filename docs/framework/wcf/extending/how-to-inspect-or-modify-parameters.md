---
title: "Como inspecionar ou modificar parâmetros"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f1a0ef31ba074082e4c3aa8a26e6a59502a7566
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-inspect-or-modify-parameters"></a>Como inspecionar ou modificar parâmetros
Você pode inspecionar ou modificar as mensagens de entrada ou saídas para uma única operação em um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] o objeto de cliente ou um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço implementando o <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface e inseri-lo no tempo de execução do cliente ou serviço. Normalmente um comportamento de operação é usado para adicionar inspetores de parâmetro para uma única operação; outros comportamentos podem ser usados para fornecer acesso fácil para o tempo de execução em um escopo maior. Para obter mais informações, consulte [estendendo clientes](../../../../docs/framework/wcf/extending/extending-clients.md) e [estendendo Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md).  
  
### <a name="inspecting-or-modifying-parameters"></a>Inspecionar ou modificar parâmetros  
  
1.  Implementar a interface <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>.  
  
2.  Implementar um <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (dependendo do escopo necessário) para adicionar o Inspetor de parâmetro como o <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> propriedades.  
  
3.  Insira seu comportamento antes de chamar <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> método o <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Para obter detalhes, consulte [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Exemplo  
 Os exemplos de código a seguir mostram, em ordem:  
  
-   Uma implementação de Inspetor de parâmetro.  
  
-   A implementação de comportamento que insere o Inspetor de parâmetro usando um <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>e um <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.  
  
-   Um arquivo de configuração que carrega e executa o comportamento de ponto de extremidade em um aplicativo cliente para inserir o Inspetor de parâmetro no cliente.  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a>Consulte também  
 [Configurando e estendendo o tempo de execução com comportamentos](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
