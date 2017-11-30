---
title: '@ServiceHost'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ed64a90131fcd8f2d9f2120c03db4a21d8dc6efe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="servicehost"></a>@ServiceHost
<span data-ttu-id="4d2ef-101">Associa a fábrica usada para produzir o host de serviço com o serviço hospedado e outros aspectos de programação necessários para acessar ou compilar o código de hospedagem fornecido no arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="4d2ef-101">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d2ef-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4d2ef-102">Syntax</span></span>  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a><span data-ttu-id="4d2ef-103">Atributos</span><span class="sxs-lookup"><span data-stu-id="4d2ef-103">Attributes</span></span>  
  
#### <a name="service"></a><span data-ttu-id="4d2ef-104">Serviço</span><span class="sxs-lookup"><span data-stu-id="4d2ef-104">Service</span></span>  
 <span data-ttu-id="4d2ef-105">O nome do tipo CLR do serviço hospedado.</span><span class="sxs-lookup"><span data-stu-id="4d2ef-105">The CLR type name of the service hosted.</span></span> <span data-ttu-id="4d2ef-106">Isso deve ser um nome qualificado de um tipo que implementa um ou mais dos contatos de serviço.</span><span class="sxs-lookup"><span data-stu-id="4d2ef-106">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>  
  
#### <a name="factory"></a><span data-ttu-id="4d2ef-107">fábrica</span><span class="sxs-lookup"><span data-stu-id="4d2ef-107">Factory</span></span>  
 <span data-ttu-id="4d2ef-108">O nome do tipo CLR da fábrica de host de serviço usado para instanciar o host de serviço.</span><span class="sxs-lookup"><span data-stu-id="4d2ef-108">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="4d2ef-109">Esse atributo é opcional.</span><span class="sxs-lookup"><span data-stu-id="4d2ef-109">This attribute is optional.</span></span> <span data-ttu-id="4d2ef-110">Se não for especificado, o padrão <xref:System.ServiceModel.Activation.ServiceHostFactory> for usado, que retorna uma instância de <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="4d2ef-110">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
#### <a name="debug"></a><span data-ttu-id="4d2ef-111">Depurar</span><span class="sxs-lookup"><span data-stu-id="4d2ef-111">Debug</span></span>  
 <span data-ttu-id="4d2ef-112">Indica se o [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] serviço deve ser compilado com símbolos de depuração.</span><span class="sxs-lookup"><span data-stu-id="4d2ef-112">Indicates whether the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service should be compiled with debug symbols.</span></span> <span data-ttu-id="4d2ef-113">`true`Se o [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] serviço deve ser compilada com símbolos de depuração; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="4d2ef-113">`true` if the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service should be compiled with debug symbols; otherwise, `false`.</span></span>  
  
#### <a name="language"></a><span data-ttu-id="4d2ef-114">Linguagem</span><span class="sxs-lookup"><span data-stu-id="4d2ef-114">Language</span></span>  
 <span data-ttu-id="4d2ef-115">Especifica o idioma usado ao compilar todo o código embutido no arquivo (. svc).</span><span class="sxs-lookup"><span data-stu-id="4d2ef-115">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="4d2ef-116">Os valores podem representar qualquer. Idiomas com suporte a rede, incluindo c#, VB e JS, que se referem a c#, Visual Basic .NET e JScript .NET, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="4d2ef-116">The values can represent any .NET-supported language, including C#, VB, and JS, which refer to C#, Visual Basic .NET, and JScript .NET, respectively.</span></span> <span data-ttu-id="4d2ef-117">Esse atributo é opcional.</span><span class="sxs-lookup"><span data-stu-id="4d2ef-117">This attribute is optional.</span></span>  
  
#### <a name="codebehind"></a><span data-ttu-id="4d2ef-118">Code-behind</span><span class="sxs-lookup"><span data-stu-id="4d2ef-118">CodeBehind</span></span>  
 <span data-ttu-id="4d2ef-119">Especifica o arquivo de origem que implementa o serviço Web XML, quando a classe que implementa o serviço Web XML não residem no mesmo arquivo e não foi compilada em um assembly e colocada no diretório \Bin.</span><span class="sxs-lookup"><span data-stu-id="4d2ef-119">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the \Bin directory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d2ef-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="4d2ef-120">Remarks</span></span>  
 <span data-ttu-id="4d2ef-121">O <xref:System.ServiceModel.ServiceHost> usado para hospedar o serviço é um ponto de extensibilidade dentro de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] modelo de programação.</span><span class="sxs-lookup"><span data-stu-id="4d2ef-121">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] programming model.</span></span> <span data-ttu-id="4d2ef-122">Um padrão de fábrica é usado para instanciar o <xref:System.ServiceModel.ServiceHost> porque ele é, potencialmente, um tipo polimórfico que o ambiente de hospedagem não deve instanciar diretamente.</span><span class="sxs-lookup"><span data-stu-id="4d2ef-122">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>  
  
 <span data-ttu-id="4d2ef-123">A implementação padrão usa <xref:System.ServiceModel.Activation.ServiceHostFactory> para criar uma instância de <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="4d2ef-123">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="4d2ef-124">Mas você pode fornecer sua própria fábrica (aquele retorna seu host derivada), especificando o nome de tipo CLR da sua implementação de fábrica no [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) diretiva.</span><span class="sxs-lookup"><span data-stu-id="4d2ef-124">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive.</span></span>  
  
 <span data-ttu-id="4d2ef-125">Para usar fábrica do host de serviço personalizado próprio em vez de fábrica padrão, forneça apenas o nome do tipo no [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) diretiva da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="4d2ef-125">To use you own custom service host factory instead of the default factory, just provide the type name in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive as follows:</span></span>  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="4d2ef-126">Mantenha as implementações de fábrica o mais leves possível.</span><span class="sxs-lookup"><span data-stu-id="4d2ef-126">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="4d2ef-127">Se você tiver muita lógica personalizada, seu código será mais reutilizável se você colocar essa lógica em seu host em vez de dentro de fábrica.</span><span class="sxs-lookup"><span data-stu-id="4d2ef-127">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>  
  
 <span data-ttu-id="4d2ef-128">Por exemplo, para habilitar um ponto de extremidade habilitado para AJAX para `MyService`, especifique o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> para o valor da `Factory` atributo, em vez do padrão <xref:System.ServiceModel.Activation.ServiceHostFactory>, no [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) diretiva como como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4d2ef-128">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d2ef-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d2ef-129">Example</span></span>  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d2ef-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d2ef-130">See Also</span></span>  
 [<span data-ttu-id="4d2ef-131">Host de serviço personalizado</span><span class="sxs-lookup"><span data-stu-id="4d2ef-131">Custom Service Host</span></span>](../../../../../docs/framework/wcf/samples/custom-service-host.md)