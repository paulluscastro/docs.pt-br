---
title: MSMQ
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9fca29f-fa44-4ec4-bb48-b10800694500
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e72d3e400440b830b689f476753a7c8c40fe2586
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="msmq"></a>MSMQ
Em um aplicativo do MSMQ, nenhuma atividade adicional é transferida do canal em fila MSMQ e MSMQ no canal em fila.  
  
 Além disso, a ID de mensagem do MSMQ e a ID de mensagem SOAP (junto com a ID da atividade, se houver) são rastreadas como parte de rastreamentos de canal em fila em uma operação de envio.  
  
 ID de mensagem do MSMQ e a ID de mensagem SOAP (juntamente com a atividade de ID, se existe) são rastreadas como parte de rastreamentos de canal em fila em uma operação de recebimento.  
  
 As transferências necessárias na operação de recebimento são executadas da mesma forma para qualquer outro transporte (receber bytes de mensagem de processo -> -> operação).
