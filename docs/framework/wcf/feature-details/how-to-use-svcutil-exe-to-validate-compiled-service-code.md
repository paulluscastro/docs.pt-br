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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8ea14631208f755b45a27ff323b7d875c1ae5cd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a><span data-ttu-id="4db90-102">Como usar o Svcutil.exe para validar o código de serviço compilado</span><span class="sxs-lookup"><span data-stu-id="4db90-102">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>
<span data-ttu-id="4db90-103">Você pode usar o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para detectar erros nas configurações e implementações de serviço sem o serviço de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="4db90-103">You can use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to detect errors in service implementations and configurations without hosting the service.</span></span>  
  
### <a name="to-validate-a-service"></a><span data-ttu-id="4db90-104">Para validar um serviço</span><span class="sxs-lookup"><span data-stu-id="4db90-104">To validate a service</span></span>  
  
1.  <span data-ttu-id="4db90-105">Compile seu serviço em um arquivo executável e um ou mais assemblies dependentes.</span><span class="sxs-lookup"><span data-stu-id="4db90-105">Compile your service into an executable file and one or more dependent assemblies.</span></span>  
  
2.  <span data-ttu-id="4db90-106">Abra um prompt de comando do SDK</span><span class="sxs-lookup"><span data-stu-id="4db90-106">Open an SDK command prompt</span></span>  
  
3.  <span data-ttu-id="4db90-107">No prompt de comando, inicie a ferramenta Svcutil.exe usando o seguinte formato.</span><span class="sxs-lookup"><span data-stu-id="4db90-107">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span> <span data-ttu-id="4db90-108">Para obter mais informações sobre os vários parâmetros, consulte Validationsection o serviço do [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="4db90-108">For more information on the various parameters, see the Service Validationsection of the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) topic.</span></span>  
  
    ```  
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="4db90-109">Você deve usar o `/serviceName` opção para indicar o nome da configuração do serviço que você deseja validar.</span><span class="sxs-lookup"><span data-stu-id="4db90-109">You must use the `/serviceName` option to indicate the configuration name of the service you want to validate.</span></span>  
  
     <span data-ttu-id="4db90-110">O `assemblyPath` argumento especifica o caminho para o arquivo executável para o serviço e um ou mais assemblies que contêm os tipos de serviço a ser validado.</span><span class="sxs-lookup"><span data-stu-id="4db90-110">The `assemblyPath` argument specifies the path to the executable file for the service and one or more assemblies that contain the service types to be validated.</span></span> <span data-ttu-id="4db90-111">O assembly executável deve ter um arquivo de configuração associado para fornecer a configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="4db90-111">The executable assembly must have an associated configuration file to provide the service configuration.</span></span> <span data-ttu-id="4db90-112">Você pode usar curingas de linha de comando padrão para fornecer vários assemblies.</span><span class="sxs-lookup"><span data-stu-id="4db90-112">You can use standard command-line wildcards to provide multiple assemblies.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4db90-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4db90-113">Example</span></span>  
 <span data-ttu-id="4db90-114">O comando a seguir o serviço myServiceName implementado no arquivo executável myServiceHost.exe.</span><span class="sxs-lookup"><span data-stu-id="4db90-114">The following command the service myServiceName implemented in the myServiceHost.exe executable file.</span></span>  <span data-ttu-id="4db90-115">O arquivo de configuração para o serviço (myServiceHost.exe.config) é carregado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="4db90-115">The configuration file for the service (myServiceHost.exe.config) is automatically loaded.</span></span>  
  
```  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="4db90-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4db90-116">See Also</span></span>  
 <span data-ttu-id="4db90-117">[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)]</span><span class="sxs-lookup"><span data-stu-id="4db90-117">[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)</span></span>