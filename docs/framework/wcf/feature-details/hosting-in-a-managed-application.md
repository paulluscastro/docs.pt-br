---
title: Hospedagem em um aplicativo gerenciado
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4e2afa9e868c1f561aed699a2bdf7d09c17898b3
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="hosting-in-a-managed-application"></a>Hospedagem em um aplicativo gerenciado
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] os serviços podem ser hospedados em qualquer [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplicativo. Os serviços de hospedagem é a opção de hospedagem mais flexível porque ela exige a menor infra-estrutura para implantar. No entanto, também é a opção de hospedagem menos eficiente, porque os aplicativos gerenciados não fornecem recursos avançados de hospedagem e gerenciamento de outras opções de hospedagem em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], como serviços de informações da Internet (IIS) e serviços do Windows.  
  
 Para criar um serviço auto-hospedado, crie e abra uma instância do <xref:System.ServiceModel.ServiceHost>, que inicia um serviço de escuta de mensagens. Para obter mais informações, consulte [como: hospedar um serviço WCF em um aplicativo gerenciado](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Para obter um exemplo completo sobre como definir um contrato, implemente o contrato e hospedar um serviço dentro de um aplicativo gerenciado, consulte o [Tutorial de Introdução](../../../../docs/framework/wcf/getting-started-tutorial.md) e [auto-host](../../../../docs/framework/wcf/samples/self-host.md).  
  
 As seções a seguir descrevem cenários comuns que usam essa opção de hospedagem.  
  
## <a name="console-applications"></a>Aplicativos de console  
 Cenários comuns que é de hospedagem interna permite [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços em execução dentro de aplicativos de console. Hospedando um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço dentro de um aplicativo de console é normalmente útil durante a fase de desenvolvimento do serviço. Isso os torna fácil depurar obter informações de rastreamento para descobrir o que está acontecendo no aplicativo e fácil de mover copiando-os para novos locais.  
  
## <a name="rich-client-applications"></a>Aplicativos de cliente avançado  
 Outros cenários comuns que permite a auto-hospedagem são aplicativos cliente avançados, como aqueles baseados em Windows Presentation Foundation (WPF) ou Windows Forms (WinForms). Essa opção de hospedagem também torna mais fácil para aplicativos cliente avançados, como [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] e aplicativos WinForms, para se comunicar com o mundo exterior. Por exemplo, um cliente de colaboração ponto a ponto que usa [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] para sua interface do usuário e também hospeda um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço que permite que outros clientes para se conectar a ele e compartilhar informações.  
  
## <a name="see-also"></a>Consulte também  
 [Hospedando serviços](../../../../docs/framework/wcf/hosting-services.md)  
 [Tutorial de Introdução](../../../../docs/framework/wcf/getting-started-tutorial.md)
