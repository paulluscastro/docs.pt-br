---
title: "Como registrar retornos de chamada para solicitações de cancelamento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b71ebee3a28fb6a829edf657f56e54799097f351
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a>Como registrar retornos de chamada para solicitações de cancelamento
O exemplo a seguir mostra como registrar um delegado que será invocado quando uma propriedade <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> tornar-se verdadeira, devido a uma chamada para <xref:System.Threading.CancellationTokenSource.Cancel%2A> no objeto que criou o token. Use essa técnica para cancelar operações assíncronas que não dão suporte nativo à estrutura de cancelamento unificada e a métodos de desbloqueio que podem estar aguardando a conclusão de uma operação assíncrona.  
  
> [!NOTE]
>  Se a opção "Apenas Meu Código" estiver habilitada, o Visual Studio em alguns casos interromperá na linha que lança a exceção e exibirá uma mensagem de erro que diz "exceção não tratada pelo código do usuário". Esse erro é benigno. Você pode pressionar F5 para continuar a partir daí e ver o comportamento de tratamento de exceção, demonstrado nos exemplos a seguir. Para impedir que o Visual Studio seja interrompido no primeiro erro, basta desmarcar a caixa de seleção "Apenas Meu Código" em **Ferramentas, Opções, Depuração, Geral**.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o método <xref:System.Net.WebClient.CancelAsync%2A> é registrado como o método a ser invocado quando o cancelamento é solicitado por meio do token de cancelamento.  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 Se o cancelamento já tiver sido solicitado quando o retorno de chamada for registrado, ainda haverá garantia de chamada do retorno de chamada. Nesse caso específico, o método <xref:System.Net.WebClient.CancelAsync%2A> não fará nada se nenhuma operação assíncrona estiver em andamento, portanto, é seguro sempre chamar o método.  
  
## <a name="see-also"></a>Consulte também  
 [Cancelamento em threads gerenciados](../../../docs/standard/threading/cancellation-in-managed-threads.md)
