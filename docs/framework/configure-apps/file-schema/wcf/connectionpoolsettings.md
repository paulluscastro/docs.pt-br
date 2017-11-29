---
title: '&lt;connectionPoolSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a43b2719606321fe77bb9b017c6a4304ba02f7a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltconnectionpoolsettingsgt"></a><span data-ttu-id="bc0cf-102">&lt;connectionPoolSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="bc0cf-102">&lt;connectionPoolSettings&gt;</span></span>
<span data-ttu-id="bc0cf-103">Especifica as configurações do pool de conexão adicionais para uma associação de Pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="bc0cf-103">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
 <span data-ttu-id="bc0cf-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="bc0cf-104">\<system.serviceModel></span></span>  
<span data-ttu-id="bc0cf-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="bc0cf-105">\<bindings></span></span>  
<span data-ttu-id="bc0cf-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="bc0cf-106">\<customBinding></span></span>  
<span data-ttu-id="bc0cf-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="bc0cf-107">\<binding></span></span>  
<span data-ttu-id="bc0cf-108">\<namePipeTransport ></span><span class="sxs-lookup"><span data-stu-id="bc0cf-108">\<namePipeTransport></span></span>  
<span data-ttu-id="bc0cf-109">\<connectionPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="bc0cf-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc0cf-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bc0cf-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings  
        groupName="String"  
    idleTimeout"TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc0cf-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bc0cf-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bc0cf-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bc0cf-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc0cf-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="bc0cf-113">Attributes</span></span>  
  
|<span data-ttu-id="bc0cf-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="bc0cf-114">Attribute</span></span>|<span data-ttu-id="bc0cf-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc0cf-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="bc0cf-116">Uma cadeia de caracteres que define o nome do pool de conexão usado para canais de saída.</span><span class="sxs-lookup"><span data-stu-id="bc0cf-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="bc0cf-117">No modo de fluxo, conexões não são compartilhados, o que significa que o pool de conexão está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="bc0cf-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="bc0cf-118">O padrão é uma cadeia de caracteres "padrão".</span><span class="sxs-lookup"><span data-stu-id="bc0cf-118">The default is a "default" string.</span></span> <span data-ttu-id="bc0cf-119">Você pode modificar esse valor para isolar as conexões para um determinado cliente em grupos separados.</span><span class="sxs-lookup"><span data-stu-id="bc0cf-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="bc0cf-120">Um positivo <xref:System.TimeSpan> que especifica o tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.</span><span class="sxs-lookup"><span data-stu-id="bc0cf-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="bc0cf-121">O padrão é 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="bc0cf-121">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="bc0cf-122">Um inteiro positivo que especifica o número máximo de conexões para um ponto de extremidade remoto iniciado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="bc0cf-122">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="bc0cf-123">Conexões ultrapassem o limite são enfileiradas até que um espaço abaixo do limite se torne disponível.</span><span class="sxs-lookup"><span data-stu-id="bc0cf-123">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="bc0cf-124">O `idleTimeout` limita a duração em que conexões permanecem na fila antes de uma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="bc0cf-124">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="bc0cf-125">O padrão é 10.</span><span class="sxs-lookup"><span data-stu-id="bc0cf-125">The default is 10.</span></span><br /><br /> <span data-ttu-id="bc0cf-126">Esse atributo limita o número de conexões ativas simultâneas do cliente para um ponto de extremidade de serviço específico.</span><span class="sxs-lookup"><span data-stu-id="bc0cf-126">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="bc0cf-127">Se esse valor for excedido fazendo mais ativas conexões de cliente, o serviço pode parecer não estar respondendo ao cliente.</span><span class="sxs-lookup"><span data-stu-id="bc0cf-127">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="bc0cf-128">Nesse caso, esse valor deverá ser ajustado para exceder o número máximo de conexões de cliente simultâneas esperado para um ponto de extremidade específico.</span><span class="sxs-lookup"><span data-stu-id="bc0cf-128">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc0cf-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bc0cf-129">Child Elements</span></span>  
 <span data-ttu-id="bc0cf-130">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="bc0cf-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc0cf-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bc0cf-131">Parent Elements</span></span>  
  
|<span data-ttu-id="bc0cf-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="bc0cf-132">Element</span></span>|<span data-ttu-id="bc0cf-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc0cf-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc0cf-134">\<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="bc0cf-134">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="bc0cf-135">Define um transporte que faz com que um canal transferir mensagens usando pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="bc0cf-135">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc0cf-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc0cf-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="bc0cf-137">Transportes</span><span class="sxs-lookup"><span data-stu-id="bc0cf-137">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="bc0cf-138">Selecionando um transporte</span><span class="sxs-lookup"><span data-stu-id="bc0cf-138">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 <span data-ttu-id="bc0cf-139">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="bc0cf-139">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="bc0cf-140">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="bc0cf-140">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="bc0cf-141">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="bc0cf-141">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="bc0cf-142">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="bc0cf-142">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)