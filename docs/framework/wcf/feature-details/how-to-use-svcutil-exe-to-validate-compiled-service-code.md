---
title: "Como usar o Svcutil.exe para validar o código de serviço compilado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b60356bd66a49c9599a8e0a9138d3b92dbe0b23c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a>Como usar o Svcutil.exe para validar o código de serviço compilado
Você pode usar o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para detectar erros nas configurações e implementações de serviço sem o serviço de hospedagem.  
  
### <a name="to-validate-a-service"></a>Para validar um serviço  
  
1.  Compile seu serviço em um arquivo executável e um ou mais assemblies dependentes.  
  
2.  Abra um prompt de comando do SDK  
  
3.  No prompt de comando, inicie a ferramenta Svcutil.exe usando o seguinte formato. Para obter mais informações sobre os vários parâmetros, consulte Validationsection o serviço do [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tópico.  
  
    ```  
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     Você deve usar o `/serviceName` opção para indicar o nome da configuração do serviço que você deseja validar.  
  
     O `assemblyPath` argumento especifica o caminho para o arquivo executável para o serviço e um ou mais assemblies que contêm os tipos de serviço a ser validado. O assembly executável deve ter um arquivo de configuração associado para fornecer a configuração do serviço. Você pode usar curingas de linha de comando padrão para fornecer vários assemblies.  
  
## <a name="example"></a>Exemplo  
 O comando a seguir o serviço myServiceName implementado no arquivo executável myServiceHost.exe.  O arquivo de configuração para o serviço (myServiceHost.exe.config) é carregado automaticamente.  
  
```  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a>Consulte também  
 [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
