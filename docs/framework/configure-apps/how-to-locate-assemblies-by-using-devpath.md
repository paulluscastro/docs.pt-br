---
title: Como localizar assemblies usando DEVPATH
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 70448f7ce4c00274dde14bace603e5c8852bf148
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a><span data-ttu-id="1686f-102">Como localizar assemblies usando DEVPATH</span><span class="sxs-lookup"><span data-stu-id="1686f-102">How to: Locate Assemblies by Using DEVPATH</span></span>
<span data-ttu-id="1686f-103">Os desenvolvedores talvez queira certificar-se de que um assembly compartilhado que estão criando funciona corretamente com vários aplicativos.</span><span class="sxs-lookup"><span data-stu-id="1686f-103">Developers might want to make sure that a shared assembly they are building works correctly with multiple applications.</span></span> <span data-ttu-id="1686f-104">Em vez de continuamente colocar o assembly no cache de assembly global durante o ciclo de desenvolvimento, o desenvolvedor pode criar uma variável de ambiente DEVPATH que aponta para o diretório de saída de compilação para o assembly.</span><span class="sxs-lookup"><span data-stu-id="1686f-104">Instead of continually putting the assembly in the global assembly cache during the development cycle, the developer can create a DEVPATH environment variable that points to the build output directory for the assembly.</span></span>  
  
 <span data-ttu-id="1686f-105">Por exemplo, suponha que você esteja criando um assembly compartilhado chamado MySharedAssembly e o diretório de saída é C:\MySharedAssembly\Debug.</span><span class="sxs-lookup"><span data-stu-id="1686f-105">For example, assume that you are building a shared assembly called MySharedAssembly and the output directory is C:\MySharedAssembly\Debug.</span></span> <span data-ttu-id="1686f-106">Você pode colocar C:\MySharedAssembly\Debug na variável DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="1686f-106">You can put C:\MySharedAssembly\Debug in the DEVPATH variable.</span></span> <span data-ttu-id="1686f-107">Você deve especificar o [ \<developmentMode >](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) elemento no arquivo de configuração da máquina.</span><span class="sxs-lookup"><span data-stu-id="1686f-107">You must then specify the [\<developmentMode>](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) element in the machine configuration file.</span></span> <span data-ttu-id="1686f-108">Esse elemento indica o common language runtime para usar DEVPATH para localizar assemblies.</span><span class="sxs-lookup"><span data-stu-id="1686f-108">This element tells the common language runtime to use DEVPATH to locate assemblies.</span></span>  
  
 <span data-ttu-id="1686f-109">O assembly compartilhado deve ser detectável pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="1686f-109">The shared assembly must be discoverable by the runtime.</span></span>  <span data-ttu-id="1686f-110">Para especificar uma pasta particular para resolver o uso de referências de assembly a [ \<codeBase > elemento](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) ou [ \<probing > elemento](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) em um arquivo de configuração, conforme descrito em [Especificando o local de um Assembly](../../../docs/framework/configure-apps/specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="1686f-110">To specify a private directory for resolving assembly references use the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) or [\<probing> Element](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) in a configuration file, as described in [Specifying an Assembly's Location](../../../docs/framework/configure-apps/specify-assembly-location.md).</span></span>  <span data-ttu-id="1686f-111">Você também pode colocar o assembly em um subdiretório do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1686f-111">You can also put the assembly in a subdirectory of the application directory.</span></span> <span data-ttu-id="1686f-112">Para saber mais, confira [Como o tempo de execução localiza os assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="1686f-112">For more information, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1686f-113">Este é um recurso avançado, destinado apenas para desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="1686f-113">This is an advanced feature, intended only for development.</span></span>  
  
 <span data-ttu-id="1686f-114">O exemplo a seguir mostra como fazer com que o tempo de execução procurar por assemblies nos diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="1686f-114">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1686f-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1686f-115">Example</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="1686f-116">Essa configuração padrão é false.</span><span class="sxs-lookup"><span data-stu-id="1686f-116">This setting defaults to false.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1686f-117">Use essa configuração somente em tempo de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="1686f-117">Use this setting only at development time.</span></span> <span data-ttu-id="1686f-118">O tempo de execução não verifica as versões em assemblies de nomes fortes encontrados no DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="1686f-118">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="1686f-119">Ele simplesmente usa o primeiro conjunto que encontrar.</span><span class="sxs-lookup"><span data-stu-id="1686f-119">It simply uses the first assembly it finds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1686f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1686f-120">See Also</span></span>  
 [<span data-ttu-id="1686f-121">Configuração de aplicativos .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1686f-121">Configuring .NET Framework Apps</span></span>](http://msdn.microsoft.com/en-us/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)