---
title: "Interfaces de fusão"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- interfaces [.NET Framework fusion]
- fusion interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], fusion
ms.assetid: e2cf98b7-40c1-4f74-86c7-8a76dd9da677
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9226eba1b9f03138180430b2abb960f43f4b4260
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="fusion-interfaces"></a>Interfaces de fusão
Esta seção descreve as interfaces não gerenciadas que a fusão API usa para acessar as propriedades de recursos do aplicativo e para localizar as versões corretas desses recursos para o aplicativo.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Interface IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)  
 Fornece métodos que geram e comparam as chaves de identidades de aplicativo e referências.  
  
 [Interface IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 Fornece uma representação de cache de assembly global.  
  
 [Interface IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)  
 Representa um único assembly no cache de assembly global.  
  
 [Interface IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)  
 Representa um enumerador para uma matriz de `IAssemblyName` objetos.  
  
 [Interface IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 Fornece métodos para descrever e trabalhar com uma identidade exclusiva de assembly.  
  
 [Interface IDefinitionAppId](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md)  
 Representa um identificador exclusivo para o código que define o aplicativo no escopo atual.  
  
 [Interface IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 Representa a assinatura exclusiva do código que define o aplicativo no escopo atual.  
  
 [Interface IEnumDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md)  
 Serve como o enumerador para uma coleção de `IDefinitionIdentity` objetos.  
  
 [Interface IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)  
 Serve como um enumerador para os atributos do objeto de código no escopo atual.  
  
 [Interface IEnumReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 Serve como um enumerador para uma coleção de `IReferenceIdentity` objetos.  
  
 [Interface IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)  
 Gerencia chaves de identidade para objetos de código.  
  
 [Interface IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)  
 Representa um enumerador para os assemblies referenciados instalados no cache de assembly global.  
  
 [Interface IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 Representa um item instalado no cache de assembly global.  
  
 [Interface IReferenceAppId](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md)  
 Representa uma referência para o identificador exclusivo para o aplicativo no escopo atual.  
  
 [Interface IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)  
 Representa uma referência para a assinatura exclusiva de um objeto de código.  
  
## <a name="reference"></a>Referência  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Funções estáticas globais de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
  
 [Enumerações de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [Estruturas de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
