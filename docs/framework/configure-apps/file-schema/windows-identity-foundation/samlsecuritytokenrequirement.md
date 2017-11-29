---
title: '&lt;samlSecurityTokenRequirement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: e0d8d467c2636f5ce95cf5fed189ae00c3ca75fb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltsamlsecuritytokenrequirementgt"></a><span data-ttu-id="cc636-102">&lt;samlSecurityTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="cc636-102">&lt;samlSecurityTokenRequirement&gt;</span></span>
<span data-ttu-id="cc636-103">Fornece configuração para o <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> classe, o <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou uma classe derivada de qualquer uma dessas classes.</span><span class="sxs-lookup"><span data-stu-id="cc636-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="cc636-104">Representado pelo <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> classe.</span><span class="sxs-lookup"><span data-stu-id="cc636-104">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
 <span data-ttu-id="cc636-105">\<System. IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="cc636-105">\<system.identityModel></span></span>  
<span data-ttu-id="cc636-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="cc636-106">\<identityConfiguration></span></span>  
<span data-ttu-id="cc636-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="cc636-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="cc636-108">\<add></span><span class="sxs-lookup"><span data-stu-id="cc636-108">\<add></span></span>  
<span data-ttu-id="cc636-109">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="cc636-109">\<samlSecurityTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc636-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cc636-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement   
            issuerCertificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
            issuerCertificateRevocationMode="NoCheck||Offline||Online"  
            issuerCertificateTrustedStoreLocation="CurrentLocation||LocalMachine"  
            issuerCertificateValidator="Namespace.Class Assembly"  
            mapToWindows=xs:boolean  
          <nameClaimType value=xs:string />  
          <roleClaimType value=xs:string />  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc636-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cc636-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cc636-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cc636-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc636-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="cc636-113">Attributes</span></span>  
  
|<span data-ttu-id="cc636-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="cc636-114">Attribute</span></span>|<span data-ttu-id="cc636-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="cc636-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cc636-116">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="cc636-116">mapToWindows</span></span>|<span data-ttu-id="cc636-117">Especifica se o manipulador de token deve mapear o token de validação para uma conta do Windows usando a declaração de UPN de entrada.</span><span class="sxs-lookup"><span data-stu-id="cc636-117">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="cc636-118">O padrão é "false".</span><span class="sxs-lookup"><span data-stu-id="cc636-118">The default is "false".</span></span>|  
|<span data-ttu-id="cc636-119">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="cc636-119">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="cc636-120">Um <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valor que especifica o modo de revogação a ser usado para o certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="cc636-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="cc636-121">O valor padrão é "Online".</span><span class="sxs-lookup"><span data-stu-id="cc636-121">The default value is "Online".</span></span>|  
|<span data-ttu-id="cc636-122">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="cc636-122">issuerCertificateValidationMode</span></span>|<span data-ttu-id="cc636-123">Um <xref:System.ServiceModel.Security.X509CertificateValidationMode> valor que especifica o modo de validação a ser usado para o certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="cc636-123">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="cc636-124">O valor padrão é "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="cc636-124">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="cc636-125">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="cc636-125">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="cc636-126">Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica o repositório de certificados x. 509.</span><span class="sxs-lookup"><span data-stu-id="cc636-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="cc636-127">O valor padrão é "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="cc636-127">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="cc636-128">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="cc636-128">issuerCertificateValidator</span></span>|<span data-ttu-id="cc636-129">Um tipo personalizado que deriva de <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="cc636-129">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="cc636-130">Se o `issuerCertificateValidationMode` atributo é "Custom", uma instância desse tipo é usada para validação de certificado do emissor.</span><span class="sxs-lookup"><span data-stu-id="cc636-130">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc636-131">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cc636-131">Child Elements</span></span>  
  
|<span data-ttu-id="cc636-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="cc636-132">Element</span></span>|<span data-ttu-id="cc636-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="cc636-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc636-134">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="cc636-134">\<nameClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/nameclaimtype.md)|<span data-ttu-id="cc636-135">Define o tipo de declaração que especifica o <xref:System.Security.Principal.IIdentity.Name%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="cc636-135">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="cc636-136">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="cc636-136">\<roleClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/roleclaimtype.md)|<span data-ttu-id="cc636-137">Especifica o tipo de declaração que define as declarações de tipo de função na coleção de <xref:System.Security.Claims.ClaimsIdentity> objetos retornados pelo <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> método do manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="cc636-137">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cc636-138">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cc636-138">Parent Elements</span></span>  
  
|<span data-ttu-id="cc636-139">Elemento</span><span class="sxs-lookup"><span data-stu-id="cc636-139">Element</span></span>|<span data-ttu-id="cc636-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="cc636-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc636-141">\<add></span><span class="sxs-lookup"><span data-stu-id="cc636-141">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="cc636-142">Adiciona o manipulador de token de segurança especificados na coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="cc636-142">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc636-143">Comentários</span><span class="sxs-lookup"><span data-stu-id="cc636-143">Remarks</span></span>  
 <span data-ttu-id="cc636-144">O `<samlSecurityTokenRequirement>` elemento é representado pelo <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> no modelo de objeto de classe e é usado para configurar o `SamlSecurityTokenRequirement` propriedade em um <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> ou <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="cc636-144">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc636-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cc636-145">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement issuerCertificateValidationMode="PeerOrChainTrust"  
                                  issuerCertificateRevocationMode="Online"  
                                  issuerCertificateTrustedStoreLocation="LocalMachine"  
                                  mapToWindows="false">  
  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```