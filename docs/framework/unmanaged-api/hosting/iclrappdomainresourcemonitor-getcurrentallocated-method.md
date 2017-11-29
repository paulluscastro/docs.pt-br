---
title: "Método ICLRAppDomainResourceMonitor::GetCurrentAllocated"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAppDomainResourceMonitor.GetCurrentAllocated
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAppDomainResourceMonitor::GetCurrentAllocated
helpviewer_keywords:
- GetCurrentAllocated method [.NET Framework hosting]
- ICLRAppDomainResourceMonitor::GetCurrentAllocated method [.NET Framework hosting]
ms.assetid: 7bab209c-efd4-44c2-af30-61abab0ae2fc
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dee616e1fbd071662a42af856fa2cd51f7bdd5d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="941c6-102">Método ICLRAppDomainResourceMonitor::GetCurrentAllocated</span><span class="sxs-lookup"><span data-stu-id="941c6-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>
<span data-ttu-id="941c6-103">Obtém o tamanho total, em bytes, de todas as alocações de memória que foram feitas pelo domínio do aplicativo desde que ele foi criado, sem subtrair a memória foi coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="941c6-103">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="941c6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="941c6-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="941c6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="941c6-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="941c6-106">[in] A ID do domínio do aplicativo solicitado.</span><span class="sxs-lookup"><span data-stu-id="941c6-106">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="941c6-107">[out] Um ponteiro para o tamanho total de todas as alocações de memória.</span><span class="sxs-lookup"><span data-stu-id="941c6-107">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="941c6-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="941c6-108">Return Value</span></span>  
 <span data-ttu-id="941c6-109">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="941c6-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="941c6-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="941c6-110">HRESULT</span></span>|<span data-ttu-id="941c6-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="941c6-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="941c6-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="941c6-112">S_OK</span></span>|<span data-ttu-id="941c6-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="941c6-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="941c6-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="941c6-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="941c6-115">O domínio de aplicativo foi descarregado ou não existe.</span><span class="sxs-lookup"><span data-stu-id="941c6-115">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="941c6-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="941c6-116">Remarks</span></span>  
 <span data-ttu-id="941c6-117">Esse método é o equivalente não gerenciado a gerenciado <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="941c6-117">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="941c6-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="941c6-118">Requirements</span></span>  
 <span data-ttu-id="941c6-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="941c6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="941c6-120">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="941c6-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="941c6-121">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="941c6-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="941c6-122">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="941c6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="941c6-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="941c6-123">See Also</span></span>  
 [<span data-ttu-id="941c6-124">Interface ICLRAppDomainResourceMonitor</span><span class="sxs-lookup"><span data-stu-id="941c6-124">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [<span data-ttu-id="941c6-125">Monitoramento de recursos de domínio do aplicativo</span><span class="sxs-lookup"><span data-stu-id="941c6-125">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="941c6-126">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="941c6-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="941c6-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="941c6-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)