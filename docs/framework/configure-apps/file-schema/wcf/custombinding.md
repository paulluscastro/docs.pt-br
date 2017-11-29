---
title: '&lt;customBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9da4f960-f64e-4d8a-894d-2b09eba5ce4b
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7f73ad4d09e085040e006102e5b44664ece98a58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcustombindinggt"></a><span data-ttu-id="6b471-102">&lt;customBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="6b471-102">&lt;customBinding&gt;</span></span>
<span data-ttu-id="6b471-103">Fornece controle total sobre a pilha de mensagens para o usuário.</span><span class="sxs-lookup"><span data-stu-id="6b471-103">Provides full control over the messaging stack for the user.</span></span>  
  
 <span data-ttu-id="6b471-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="6b471-104">\<system.serviceModel></span></span>  
<span data-ttu-id="6b471-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="6b471-105">\<bindings></span></span>  
<span data-ttu-id="6b471-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="6b471-106">\<customBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b471-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6b471-107">Syntax</span></span>  
  
```xml  
<customBinding>  
    <binding name="string"  
        closeTimeout="TimeSpan"  
        openTimeout="TimeSpan"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
       <compositeDuplex clientBaseAddress="Uri"/>  
       <reliableSession acknowledgementInterval="TimeSpan"  
           advancedFlowControl="Boolean"   
           bufferedMessagesQuota="Integer"  
           inactivityTimeout="TimeSpan"  
           maxPendingChannels="Integer"  
           maxRetryCount="Integer"   
           ordered="Boolean" />  
       <pnrpPeerResolver />  
       <windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
       <sslStreamSecurity requireClientCertificate="Boolean" />  
              <transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"/>  
       <security   
          defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
           authenticationMode="UserNameForAnonymous"  
           contextMode="Cookie"   
           defaultProtectionLevel="Sign"  
           enableKeyDerivation="false"  
           keyEntropyMode="ClientEntropy"   
                  messageProtectionOrder="SignBeforeEncryptAndEncryptSignature"   
           securityVersion="WSSecurityXXX2005">  
           <localClientSettings cacheCookies="false"  
               detectReplays="false"  
               maxCookieCachingTime="00:07:24" />  
           <localServiceSettings replayCacheSize="9"  
               maxClockSkew="00:00:03"   
               replayWindow="00:07:22.2190000" />  
       </security>  
       <binaryMessageEncoding maxReadPoolSize="Integer"  
           maxWritePoolSize="Integer"  
           maxSessionSize="Integer" />  
       <httpsTransport manualAddressing="Boolean"  
           maxMessageSize="Integer"  
           authenticationScheme="Negotiate"   
           bypassProxyOnLocal="Boolean"  
           hostNameComparisonMode="Exact"   
           mapAddressingHeadersToHttpHeaders="Boolean"   
           proxyaddress="Uri"  
           realm="String"   
           requireClientCertificate="Boolean" />  
       <peerTransport manualAddressing="false"  
          maxMessageSize="20002"  
          listenIPAddress="202.10.1.9"   
          messageAuthentication="false"  
          peerNodeAuthenticationMode="None"  
          port="1000" />  
  
<security   
      defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
   authenticationMode="UserNameForAnonymous"  
   bootstrapBindingConfiguration="String"  
   bootstrapBindingSectionName="String"  
   defaultProtectionLevel="None/Sign/EncryptAndSign"  
      requireDerivedKeys="Boolean"  
   securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"  
   includeTimestamp="Boolean"  
   keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"   
   messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"   
   protectTokens="Boolean"  
   requireSecurityContextCancellation="Boolean"  
   securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"  
   requireSignatureConfirmation="Boolean" >  
   <localClientSettings cacheCookies="Boolean"  
      detectReplays="Boolean"  
      replayCacheSize="Integer"  
      maxClockSkew="TimeSpan"  
      maxCookieCachingTime="TimeSpan"  
      replayWindow="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      reconnectOnTransportFailure="Boolean"  
      timestampValidityDuration="TimeSpan"  
      cookieRenewalThresholdPercentage="Integer" />  
   <localServiceSettings detectReplays="Boolean"  
      issuedCookieLifeTime="TimeSpan"  
      maxStatefulNegotiations="Integer"  
            replayCacheSize="Integer"  
      maxClockSkew="TimeSpan"   
      negotiationTimeout="TimeSpan"  
      replayWindow="TimeSpan"  
      inactivityTimeout="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      reconnectOnTransportFailure="Boolean"  
      maxConcurrentSessions="Integer"  
      timestampValidityDuration="TimeSpan" />  
   <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />  
<security   
   defaultAlgorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/ Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
   authenticationMode="UserNameForAnonymous"  
   bootstrapBindingConfiguration="String"  
   bootstrapBindingSectionName="String"  
   defaultProtectionLevel="None/Sign/EncryptAndSign"  
      requireDerivedKeys="Boolean"  
   securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast"  
   includeTimestamp="Boolean"  
   keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"   
   messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"   
   protectTokens="Boolean"  
   requireSecurityContextCancellation="Boolean"  
   securityVersion=" WSSecurityJan2004/WSSecurityXXX2005"  
   requireSignatureConfirmation="Boolean" >  
   <localClientSettings cacheCookies="Boolean"  
      detectReplays="Boolean"  
      replayCacheSize="Integer"  
      maxClockSkew="TimeSpan"  
      maxCookieCachingTime="TimeSpan"  
      replayWindow="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      reconnectOnTransportFailure="Boolean"  
      timestampValidityDuration="TimeSpan"  
      cookieRenewalThresholdPercentage="Integer" />  
   <localServiceSettings detectReplays="Boolean"  
      issuedCookieLifeTime="TimeSpan"  
      maxStatefulNegotiations="Integer"  
            replayCacheSize="Integer"  
      maxClockSkew="TimeSpan"   
      negotiationTimeout="TimeSpan"  
      replayWindow="TimeSpan"  
      inactivityTimeout="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      reconnectOnTransportFailure="Boolean"  
      maxConcurrentSessions="Integer"  
      timestampValidityDuration="TimeSpan" />  
   <federationParameters trustVersion="WSTrustApr2004/WSTrustFeb2005" />  
   <GenericIssuedTokenParameters>   
      <LocalIssuerIssuedTokenParameters keyType=" SymmeticKey/PublicKey"  
        keySize="Integer"  
        tokenType="String" />  
     <IssuedTokenParametersEndpointAddress address="URI"  
        bindingConfiguration="String"  
        binding="String" />  
     <IssuedTokenClient localIssuerChannelBehaviors="String"  
        cacheIssuedTokens="Boolean"  
        maxIssuedTokenCachingTime="TimeSpan"  
        keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy" />  
     <IssuedTokenClientBehavior issuerAddress="String"  
        behaviorConfiguration="String" />  
     <IssuedTokenClientBehavior address="URI"  
        bindingConfiguration="String"  
        binding="String" />  
   </GenericIssuedTokenParameters>   
</security>  
</binding>  
</customBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b471-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6b471-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6b471-109">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="6b471-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b471-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="6b471-110">Attributes</span></span>  
  
|<span data-ttu-id="6b471-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="6b471-111">Attribute</span></span>|<span data-ttu-id="6b471-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="6b471-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6b471-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="6b471-113">closeTimeout</span></span>|<span data-ttu-id="6b471-114">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de fechamento concluir.</span><span class="sxs-lookup"><span data-stu-id="6b471-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="6b471-115">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6b471-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6b471-116">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="6b471-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="6b471-117">name</span><span class="sxs-lookup"><span data-stu-id="6b471-117">name</span></span>|<span data-ttu-id="6b471-118">Uma cadeia de caracteres que contém o nome da configuração da associação.</span><span class="sxs-lookup"><span data-stu-id="6b471-118">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="6b471-119">Esse valor é uma cadeia de caracteres definida pelo usuário que age como a cadeia de caracteres de identificação para a associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="6b471-119">This value is a user-defined string that acts as the identification string for the custom binding.</span></span> <span data-ttu-id="6b471-120">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="6b471-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="6b471-121">Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="6b471-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="6b471-122">openTimeout</span><span class="sxs-lookup"><span data-stu-id="6b471-122">openTimeout</span></span>|<span data-ttu-id="6b471-123">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de abertura concluir.</span><span class="sxs-lookup"><span data-stu-id="6b471-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="6b471-124">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6b471-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6b471-125">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="6b471-125">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="6b471-126">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="6b471-126">receiveTimeout</span></span>|<span data-ttu-id="6b471-127">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento concluir.</span><span class="sxs-lookup"><span data-stu-id="6b471-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="6b471-128">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6b471-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6b471-129">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="6b471-129">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="6b471-130">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="6b471-130">sendTimeout</span></span>|<span data-ttu-id="6b471-131">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio concluir.</span><span class="sxs-lookup"><span data-stu-id="6b471-131">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="6b471-132">Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="6b471-132">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6b471-133">O padrão é 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="6b471-133">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b471-134">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6b471-134">Child Elements</span></span>  
  
|<span data-ttu-id="6b471-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="6b471-135">Element</span></span>|<span data-ttu-id="6b471-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="6b471-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b471-137">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="6b471-137">\<compositeDuplex></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)|<span data-ttu-id="6b471-138">Especifica a mensagem bidirecional para a associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="6b471-138">Specifies two-way messaging to the custom binding.</span></span> <span data-ttu-id="6b471-139">Ele é usado com transportes que não permitem a comunicação duplex nativamente, por exemplo, HTTP.</span><span class="sxs-lookup"><span data-stu-id="6b471-139">It is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="6b471-140">TCP, por outro lado, permite a comunicação duplex nativamente e não requer o uso desse elemento de associação para o serviço enviar mensagens para um cliente.</span><span class="sxs-lookup"><span data-stu-id="6b471-140">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span><br /><br /> <span data-ttu-id="6b471-141">O cliente deve expor um endereço para o serviço fazer contato e estabelecer uma conexão.</span><span class="sxs-lookup"><span data-stu-id="6b471-141">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="6b471-142">Este endereço de cliente é fornecido pelo `ClientBaseAddress` atributo.</span><span class="sxs-lookup"><span data-stu-id="6b471-142">This client address is provided by the `ClientBaseAddress` attribute.</span></span><br /><br /> <span data-ttu-id="6b471-143">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span><span class="sxs-lookup"><span data-stu-id="6b471-143">This element is of type <xref:System.ServiceModel.Configuration.CompositeDuplexElement>.</span></span>|  
|[<span data-ttu-id="6b471-144">\<pnrpPeerResolver ></span><span class="sxs-lookup"><span data-stu-id="6b471-144">\<pnrpPeerResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/pnrppeerresolver.md)|<span data-ttu-id="6b471-145">Especifica um resolvedor de nome de ponto de resolução protocolo PNRP (Peer Name).</span><span class="sxs-lookup"><span data-stu-id="6b471-145">Specifies a Peer Name Resolution Protocol (PNRP) peer name resolver.</span></span> <span data-ttu-id="6b471-146">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span><span class="sxs-lookup"><span data-stu-id="6b471-146">This element is of type <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>.</span></span>|  
|[<span data-ttu-id="6b471-147">\<reliableSession ></span><span class="sxs-lookup"><span data-stu-id="6b471-147">\<reliableSession></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)|<span data-ttu-id="6b471-148">Especifica a configuração para mensagens WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="6b471-148">Specifies the setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="6b471-149">Quando esse elemento é adicionado a uma associação personalizada, o canal resultante pode dar suporte a exatamente-uma vez garantias de entrega.</span><span class="sxs-lookup"><span data-stu-id="6b471-149">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span> <span data-ttu-id="6b471-150">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span><span class="sxs-lookup"><span data-stu-id="6b471-150">This element is of type <xref:System.ServiceModel.Configuration.ReliableSessionElement>.</span></span>|  
|[<span data-ttu-id="6b471-151">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="6b471-151">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="6b471-152">Especifica as opções de segurança da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="6b471-152">Specifies the options for security of the custom binding.</span></span> <span data-ttu-id="6b471-153">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.SecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="6b471-153">This element is of type <xref:System.ServiceModel.Configuration.SecurityElement>.</span></span>|  
|[<span data-ttu-id="6b471-154">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="6b471-154">\<sslStreamSecurity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)|<span data-ttu-id="6b471-155">Especifica as configurações de segurança para uma associação de fluxo SSL.</span><span class="sxs-lookup"><span data-stu-id="6b471-155">Specifies the security settings for a SSL stream binding.</span></span> <span data-ttu-id="6b471-156">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="6b471-156">This element is of type <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>.</span></span>|  
|[<span data-ttu-id="6b471-157">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="6b471-157">\<transactionFlow></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)|<span data-ttu-id="6b471-158">Especifica que a associação oferece suporte a fluxo de transações e o protocolo a ser usado pelo `transactionProtocol` atributo.</span><span class="sxs-lookup"><span data-stu-id="6b471-158">Specifies that the binding supports transaction flow, and the protocol to be used by the `transactionProtocol` attribute.</span></span> <span data-ttu-id="6b471-159">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span><span class="sxs-lookup"><span data-stu-id="6b471-159">This element is of type <xref:System.ServiceModel.Configuration.TransactionFlowElement>.</span></span>|  
|[<span data-ttu-id="6b471-160">\<windowsstreamsecurity está ></span><span class="sxs-lookup"><span data-stu-id="6b471-160">\<windowsStreamSecurity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md)|<span data-ttu-id="6b471-161">Especifica as opções de segurança da associação personalizada de streaming.</span><span class="sxs-lookup"><span data-stu-id="6b471-161">Specifies the options for streaming security of the custom binding.</span></span> <span data-ttu-id="6b471-162">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="6b471-162">This element is of type <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6b471-163">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6b471-163">Parent Elements</span></span>  
  
|<span data-ttu-id="6b471-164">Elemento</span><span class="sxs-lookup"><span data-stu-id="6b471-164">Element</span></span>|<span data-ttu-id="6b471-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="6b471-165">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b471-166">associações</span><span class="sxs-lookup"><span data-stu-id="6b471-166">bindings</span></span>|<span data-ttu-id="6b471-167">Contém todas as associações de aplicativos do Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="6b471-167">Contains all bindings for Windows Communication Foundation applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b471-168">Comentários</span><span class="sxs-lookup"><span data-stu-id="6b471-168">Remarks</span></span>  
 <span data-ttu-id="6b471-169">Associações personalizadas fornecem controle total sobre a pilha de mensagens do WCF.</span><span class="sxs-lookup"><span data-stu-id="6b471-169">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="6b471-170">Associações personalizadas especiais podem ser criadas meu adicionando os elementos de configuração para entidades específicas.</span><span class="sxs-lookup"><span data-stu-id="6b471-170">Special tailored bindings can be created my adding the configuration elements for specific entities.</span></span> <span data-ttu-id="6b471-171">Por exemplo, o usuário pode combinar o `httpsTransport` seção, `reliableSession` seção e `security` seção para criar um https segura e confiável com base em associação.</span><span class="sxs-lookup"><span data-stu-id="6b471-171">For example, the user can combine the `httpsTransport` section, `reliableSession` section and the `security` section to create a reliable and secure https based binding.</span></span>  
  
 <span data-ttu-id="6b471-172">Uma associação individual define a pilha de mensagem, especificando os elementos de configuração para os elementos da pilha na ordem em que aparecem na pilha.</span><span class="sxs-lookup"><span data-stu-id="6b471-172">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="6b471-173">Cada elemento define e configura um elemento da pilha.</span><span class="sxs-lookup"><span data-stu-id="6b471-173">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="6b471-174">Deve haver apenas um elemento de transporte em cada associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="6b471-174">There must be one and only one transport element in each custom binding.</span></span> <span data-ttu-id="6b471-175">Sem esse elemento, a pilha de mensagens está incompleta.</span><span class="sxs-lookup"><span data-stu-id="6b471-175">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="6b471-176">A ordem na qual os elementos aparecem na pilha é importante, porque é a ordem na qual as operações são aplicadas à mensagem.</span><span class="sxs-lookup"><span data-stu-id="6b471-176">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="6b471-177">A ordem recomendada de elementos da pilha é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6b471-177">The recommended order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="6b471-178">Transações (opcionais)</span><span class="sxs-lookup"><span data-stu-id="6b471-178">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="6b471-179">Confiável de mensagens (opcional)</span><span class="sxs-lookup"><span data-stu-id="6b471-179">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="6b471-180">Segurança (opcional)</span><span class="sxs-lookup"><span data-stu-id="6b471-180">Security (optional)</span></span>  
  
4.  <span data-ttu-id="6b471-181">Transporte</span><span class="sxs-lookup"><span data-stu-id="6b471-181">Transport</span></span>  
  
5.  <span data-ttu-id="6b471-182">Codificador (opcional)</span><span class="sxs-lookup"><span data-stu-id="6b471-182">Encoder (optional)</span></span>  
  
 <span data-ttu-id="6b471-183">Use uma associação personalizada quando uma das associações fornecidas pelo sistema não atende aos requisitos de seu serviço.</span><span class="sxs-lookup"><span data-stu-id="6b471-183">Use a custom binding when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="6b471-184">Uma associação personalizada pode ser usada, por exemplo, para habilitar o uso de um novo transporte ou um codificador de novo em um ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="6b471-184">A custom binding could be used, for example, to enable the use of a new transport or a new encoder at a service endpoint.</span></span>  
  
 <span data-ttu-id="6b471-185">Uma associação personalizada é criada usando uma da <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> de uma coleção de elementos que estão "empilhados" em uma ordem específica de associação:</span><span class="sxs-lookup"><span data-stu-id="6b471-185">A custom binding is constructed using one of the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> from a collection of binding elements that are "stacked" in a specific order:</span></span>  
  
-   <span data-ttu-id="6b471-186">Na parte superior é um recurso opcional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> que permite o fluxo de transações.</span><span class="sxs-lookup"><span data-stu-id="6b471-186">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> that allows flowing transactions.</span></span>  
  
-   <span data-ttu-id="6b471-187">Em seguida, é um recurso opcional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> que fornece uma sessão e o mecanismo de ordenação conforme definido na especificação WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="6b471-187">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> that provides a session and ordering mechanism as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="6b471-188">Essa noção de uma sessão pode cruzar com intermediários SOAP e transporte.</span><span class="sxs-lookup"><span data-stu-id="6b471-188">This notion of a session can cross SOAP and transport intermediaries.</span></span>  
  
-   <span data-ttu-id="6b471-189">Em seguida, é um elemento de associação de segurança opcional que fornece recursos de segurança como autenticação, autorização, proteção e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="6b471-189">Next is an optional security binding element that provides security features like authorization, authentication, protection, and confidentiality.</span></span> <span data-ttu-id="6b471-190">Os seguintes elementos de associação de segurança são fornecidos por [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="6b471-190">The following security binding elements are provided by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
-   <span data-ttu-id="6b471-191">Em seguida os padrões de mensagem opcionais são especificados pelos elementos de associação:</span><span class="sxs-lookup"><span data-stu-id="6b471-191">Next are the optional message-patterns specified by binding elements:</span></span>  
  
-   <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
  
-   <span data-ttu-id="6b471-192">Em seguida os upgrades/auxiliares de transporte opcional são elementos de associação:</span><span class="sxs-lookup"><span data-stu-id="6b471-192">Next are the optional transport upgrades/helpers binding elements:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   <span data-ttu-id="6b471-193">Em seguida, é um elemento de associação de codificação de mensagem necessário.</span><span class="sxs-lookup"><span data-stu-id="6b471-193">Next is a required message encoding binding element.</span></span> <span data-ttu-id="6b471-194">Você pode usar seu próprio transporte ou usar uma codificação associações a mensagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="6b471-194">You can use your own transport or use one of the following message encoding bindings:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
-   <span data-ttu-id="6b471-195">Na parte inferior é um elemento de transporte necessário.</span><span class="sxs-lookup"><span data-stu-id="6b471-195">At the bottom is a required transport element.</span></span> <span data-ttu-id="6b471-196">Você pode usar seu próprio transporte ou use um dos elementos fornecidos por de associação de transporte [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="6b471-196">You can use your own transport or use one of transport binding elements provided by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
    -   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
 <span data-ttu-id="6b471-197">A tabela a seguir resume as opções para cada camada.</span><span class="sxs-lookup"><span data-stu-id="6b471-197">The following table summarizes the options for each layer.</span></span>  
  
|<span data-ttu-id="6b471-198">Camada</span><span class="sxs-lookup"><span data-stu-id="6b471-198">Layer</span></span>|<span data-ttu-id="6b471-199">Opções</span><span class="sxs-lookup"><span data-stu-id="6b471-199">Options</span></span>|<span data-ttu-id="6b471-200">Necessária</span><span class="sxs-lookup"><span data-stu-id="6b471-200">Required</span></span>|  
|-----------|-------------|--------------|  
|<span data-ttu-id="6b471-201">Fluxo de transações</span><span class="sxs-lookup"><span data-stu-id="6b471-201">Transaction Flow</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="6b471-202">Não</span><span class="sxs-lookup"><span data-stu-id="6b471-202">No</span></span>|  
|<span data-ttu-id="6b471-203">Confiabilidade</span><span class="sxs-lookup"><span data-stu-id="6b471-203">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="6b471-204">Não</span><span class="sxs-lookup"><span data-stu-id="6b471-204">No</span></span>|  
|<span data-ttu-id="6b471-205">Segurança</span><span class="sxs-lookup"><span data-stu-id="6b471-205">Security</span></span>|<span data-ttu-id="6b471-206">Simétrica, assimétrica, nível de transporte</span><span class="sxs-lookup"><span data-stu-id="6b471-206">Symmetric, Asymmetric, Transport-Level</span></span>|<span data-ttu-id="6b471-207">Não</span><span class="sxs-lookup"><span data-stu-id="6b471-207">No</span></span>|  
|<span data-ttu-id="6b471-208">Alteração de forma</span><span class="sxs-lookup"><span data-stu-id="6b471-208">Shape Change</span></span>|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>|<span data-ttu-id="6b471-209">Não</span><span class="sxs-lookup"><span data-stu-id="6b471-209">No</span></span>|  
|<span data-ttu-id="6b471-210">Atualizações de transporte</span><span class="sxs-lookup"><span data-stu-id="6b471-210">Transport Upgrades</span></span>|<span data-ttu-id="6b471-211">Fluxo SSL, fluxo do Windows, resolvedor Peer</span><span class="sxs-lookup"><span data-stu-id="6b471-211">SSL stream, Windows stream, Peer Resolver</span></span>|<span data-ttu-id="6b471-212">Não</span><span class="sxs-lookup"><span data-stu-id="6b471-212">No</span></span>|  
|<span data-ttu-id="6b471-213">Codificando</span><span class="sxs-lookup"><span data-stu-id="6b471-213">Encoding</span></span>|<span data-ttu-id="6b471-214">Texto, binária, MTOM, personalizado</span><span class="sxs-lookup"><span data-stu-id="6b471-214">Text, Binary, MTOM, Custom</span></span>|<span data-ttu-id="6b471-215">Sim</span><span class="sxs-lookup"><span data-stu-id="6b471-215">Yes</span></span>|  
|<span data-ttu-id="6b471-216">Transporte</span><span class="sxs-lookup"><span data-stu-id="6b471-216">Transport</span></span>|<span data-ttu-id="6b471-217">Tipos HTTP, HTTPS, TCP, Pipes nomeados, do MSMQ, personalizadas</span><span class="sxs-lookup"><span data-stu-id="6b471-217">TCP, Named Pipes, HTTP, HTTPS, flavors of MSMQ, Custom</span></span>|<span data-ttu-id="6b471-218">Sim</span><span class="sxs-lookup"><span data-stu-id="6b471-218">Yes</span></span>|  
  
 <span data-ttu-id="6b471-219">Além disso, você pode definir seus próprios elementos de associação e inseri-los entre qualquer uma das camadas de definido anteriores.</span><span class="sxs-lookup"><span data-stu-id="6b471-219">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>  
  
 <span data-ttu-id="6b471-220">Para obter uma discussão sobre como usar uma associação para modificar uma associação fornecida pelo sistema personalizada, consulte [como: personalizar uma associação System-Provided](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="6b471-220">For a discussion on how to use a custom binding to modify a system-provided binding, see [How to: Customize a System-Provided Binding](../../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
1.  
  
## <a name="see-also"></a><span data-ttu-id="6b471-221">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b471-221">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="6b471-222">\<associação ></span><span class="sxs-lookup"><span data-stu-id="6b471-222">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 <span data-ttu-id="6b471-223">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="6b471-223">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="6b471-224">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="6b471-224">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="6b471-225">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="6b471-225">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="6b471-226">customBinding elemento</span><span class="sxs-lookup"><span data-stu-id="6b471-226">customBinding Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 <span data-ttu-id="6b471-227">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="6b471-227">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="6b471-228">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="6b471-228">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="6b471-229">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="6b471-229">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)