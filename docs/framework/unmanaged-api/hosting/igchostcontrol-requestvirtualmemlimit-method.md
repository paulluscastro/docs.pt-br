---
title: "Método IGCHostControl::RequestVirtualMemLimit"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHostControl.RequestVirtualMemLimit
api_location: mscoree.dll
api_type: COM
f1_keywords: RequestVirtualMemLimit
helpviewer_keywords:
- IGCHostControl::RequestVirtualMemLimit method [.NET Framework hosting]
- RequestVirtualMemLimit method [.NET Framework hosting]
ms.assetid: f4984a8c-4c0e-4460-9aa1-d022b3621228
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4892cf5dc3a3663f1bccc95d1975bfe96277faa5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="78cee-102">Método IGCHostControl::RequestVirtualMemLimit</span><span class="sxs-lookup"><span data-stu-id="78cee-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="78cee-103">Solicitações do host para alterar os limites de memória virtual.</span><span class="sxs-lookup"><span data-stu-id="78cee-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78cee-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="78cee-104">Syntax</span></span>  
  
```  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78cee-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="78cee-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="78cee-106">[in] O tamanho solicitado de memória a ser alocada.</span><span class="sxs-lookup"><span data-stu-id="78cee-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="78cee-107">[out no] Um ponteiro para o tamanho real da memória alocada.</span><span class="sxs-lookup"><span data-stu-id="78cee-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78cee-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="78cee-108">Requirements</span></span>  
 <span data-ttu-id="78cee-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78cee-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78cee-110">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="78cee-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="78cee-111">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="78cee-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78cee-112">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78cee-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78cee-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78cee-113">See Also</span></span>  
 [<span data-ttu-id="78cee-114">Interface IGCHostControl</span><span class="sxs-lookup"><span data-stu-id="78cee-114">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)