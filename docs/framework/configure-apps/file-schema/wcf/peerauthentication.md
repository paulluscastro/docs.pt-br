---
title: '&lt;peerAuthentication&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fd18acaf76b2d5ccceb12b62398357b0b1655cb0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltpeerauthenticationgt"></a><span data-ttu-id="e0deb-102">&lt;peerAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="e0deb-102">&lt;peerAuthentication&gt;</span></span>
<span data-ttu-id="e0deb-103">Especifica as configurações de autenticação para um certificado de ponto a ponto usado por um nó ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="e0deb-103">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
 <span data-ttu-id="e0deb-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e0deb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e0deb-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="e0deb-105">\<behaviors></span></span>  
<span data-ttu-id="e0deb-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e0deb-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e0deb-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="e0deb-107">\<behavior></span></span>  
<span data-ttu-id="e0deb-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="e0deb-108">\<serviceCredentials></span></span>  
<span data-ttu-id="e0deb-109">\<par ></span><span class="sxs-lookup"><span data-stu-id="e0deb-109">\<peer></span></span>  
<span data-ttu-id="e0deb-110">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="e0deb-110">\<peerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0deb-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0deb-111">Syntax</span></span>  
  
```xml  
<peerAuthentication  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
      certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
      revocationMode="NoCheck/Online/Offline"  
      trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0deb-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e0deb-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e0deb-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e0deb-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0deb-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="e0deb-114">Attributes</span></span>  
  
|<span data-ttu-id="e0deb-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="e0deb-115">Attribute</span></span>|<span data-ttu-id="e0deb-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="e0deb-116">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="e0deb-117">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="e0deb-117">Optional enumeration.</span></span> <span data-ttu-id="e0deb-118">Especifica um dos três modos usados para validar credenciais.</span><span class="sxs-lookup"><span data-stu-id="e0deb-118">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="e0deb-119">Esse atributo é do tipo <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="e0deb-119">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="e0deb-120">Se definido como `Custom`, em seguida, um `customCertificateValidator` também deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="e0deb-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="e0deb-121">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="e0deb-121">Optional string.</span></span> <span data-ttu-id="e0deb-122">Especifica um tipo e assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="e0deb-122">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="e0deb-123">Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom`.</span><span class="sxs-lookup"><span data-stu-id="e0deb-123">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="e0deb-124">Esse atributo é do tipo <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="e0deb-124">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="e0deb-125">Fornece um par de padrão de validador de certificado que verifica o certificado de ponto a ponto em relação ao armazenamento de pessoas confiáveis.</span><span class="sxs-lookup"><span data-stu-id="e0deb-125"> provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="e0deb-126">Ele também verifica se o certificado se encadeia uma raiz válido.</span><span class="sxs-lookup"><span data-stu-id="e0deb-126">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="e0deb-127">Você pode implementar um validador personalizado para especificar um comportamento diferente e usar esse atributo para apontar para o validador personalizado.</span><span class="sxs-lookup"><span data-stu-id="e0deb-127">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="e0deb-128">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="e0deb-128">Optional enumeration.</span></span> <span data-ttu-id="e0deb-129">Especifica o modo de revogação de certificado.</span><span class="sxs-lookup"><span data-stu-id="e0deb-129">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="e0deb-130">Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="e0deb-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="e0deb-131">O sistema verifica se o certificado de ponto a ponto não foi revogado por procurar na lista de certificados revogados.</span><span class="sxs-lookup"><span data-stu-id="e0deb-131">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="e0deb-132">Essa verificação pode ser executada através da verificação online ou em uma lista de revogação em cache.</span><span class="sxs-lookup"><span data-stu-id="e0deb-132">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="e0deb-133">Verificação de revogação pode ser desativado por configuração deste atributo como NoCheck.</span><span class="sxs-lookup"><span data-stu-id="e0deb-133">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="e0deb-134">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="e0deb-134">Optional enumeration.</span></span> <span data-ttu-id="e0deb-135">Especifica o local de armazenamento confiável em que o certificado de ponto a ponto é validado pelo [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] sistema de segurança.</span><span class="sxs-lookup"><span data-stu-id="e0deb-135">Specifies the trusted store location where the peer certificate is validated by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] security system.</span></span> <span data-ttu-id="e0deb-136">Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="e0deb-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e0deb-137">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e0deb-137">Child Elements</span></span>  
 <span data-ttu-id="e0deb-138">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e0deb-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e0deb-139">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e0deb-139">Parent Elements</span></span>  
  
|<span data-ttu-id="e0deb-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="e0deb-140">Element</span></span>|<span data-ttu-id="e0deb-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="e0deb-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0deb-142">\<par ></span><span class="sxs-lookup"><span data-stu-id="e0deb-142">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="e0deb-143">Especifica as credenciais atuais de um nó ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="e0deb-143">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0deb-144">Comentários</span><span class="sxs-lookup"><span data-stu-id="e0deb-144">Remarks</span></span>  
 <span data-ttu-id="e0deb-145">O `<authentication>` elemento corresponde à <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> classe.</span><span class="sxs-lookup"><span data-stu-id="e0deb-145">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="e0deb-146">Este elemento Especifica um validador, que é invocado durante a autenticação de vizinho de vizinho na malha.</span><span class="sxs-lookup"><span data-stu-id="e0deb-146">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="e0deb-147">Quando um novo par tenta estabelecer uma conexão vizinha, ele passa suas próprias credenciais para o par está respondendo.</span><span class="sxs-lookup"><span data-stu-id="e0deb-147">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="e0deb-148">O validador do Respondente é invocado para verificar a credencial da parte remota.</span><span class="sxs-lookup"><span data-stu-id="e0deb-148">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="e0deb-149">Sempre que uma conexão ponto a ponto é estabelecida na malha, os pontos são autenticados mutuamente, validadores significado em ambas as extremidades são invocados.</span><span class="sxs-lookup"><span data-stu-id="e0deb-149">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0deb-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0deb-150">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="e0deb-151">Trabalhar com certificados</span><span class="sxs-lookup"><span data-stu-id="e0deb-151">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="e0deb-152">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="e0deb-152">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="e0deb-153">Autenticação de mensagens de canal par</span><span class="sxs-lookup"><span data-stu-id="e0deb-153">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="e0deb-154">Autenticação personalizada de canal par</span><span class="sxs-lookup"><span data-stu-id="e0deb-154">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="e0deb-155">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="e0deb-155">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)