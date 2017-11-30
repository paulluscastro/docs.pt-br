---
title: "Método IHostSecurityManager::SetThreadToken"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.SetThreadToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::SetThreadToken
helpviewer_keywords:
- SetThreadToken method [.NET Framework hosting]
- IHostSecurityManager::SetThreadToken method [.NET Framework hosting]
ms.assetid: e951c345-8a86-4587-911b-a1a57bc6428a
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 49a505af3ef7d0208af7c65713e615fd44253e93
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a><span data-ttu-id="ac303-102">Método IHostSecurityManager::SetThreadToken</span><span class="sxs-lookup"><span data-stu-id="ac303-102">IHostSecurityManager::SetThreadToken Method</span></span>
<span data-ttu-id="ac303-103">Define um identificador para o thread em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="ac303-103">Sets a handle for the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac303-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac303-104">Syntax</span></span>  
  
```  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ac303-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ac303-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="ac303-106">[in] Um identificador para o token a ser definido para o thread em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="ac303-106">[in] A handle to the token to set for the currently executing thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac303-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ac303-107">Return Value</span></span>  
  
|<span data-ttu-id="ac303-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ac303-108">HRESULT</span></span>|<span data-ttu-id="ac303-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac303-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ac303-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ac303-110">S_OK</span></span>|<span data-ttu-id="ac303-111">`SetThreadToken`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="ac303-111">`SetThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="ac303-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ac303-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ac303-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="ac303-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ac303-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ac303-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ac303-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="ac303-115">The call timed out.</span></span>|  
|<span data-ttu-id="ac303-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ac303-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ac303-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="ac303-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ac303-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ac303-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ac303-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="ac303-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ac303-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ac303-120">E_FAIL</span></span>|<span data-ttu-id="ac303-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="ac303-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ac303-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="ac303-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ac303-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ac303-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac303-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="ac303-124">Remarks</span></span>  
 <span data-ttu-id="ac303-125">`IHostSecurityManager::SetThreadToken`se comporta da mesma forma para a função Win32 correspondente de mesmo nome, exceto que a função Win32 permite que o chamador passar um identificador para um thread arbitrário, enquanto `IHostSecurityManager::SetThreadToken` pode associar um token somente o thread em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="ac303-125">`IHostSecurityManager::SetThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::SetThreadToken` can associate a token only with the currently executing thread.</span></span>  
  
 <span data-ttu-id="ac303-126">O `HANDLE` tipo não é compatível com; isto é, seu tamanho é específico para um sistema operacional e requer empacotamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="ac303-126">The `HANDLE` type is not COM-compliant; that is, its size is specific to an operating system and it requires custom marshaling.</span></span> <span data-ttu-id="ac303-127">Portanto, esse token é para uso somente dentro do processo, entre o host e o CLR.</span><span class="sxs-lookup"><span data-stu-id="ac303-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac303-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ac303-128">Requirements</span></span>  
 <span data-ttu-id="ac303-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac303-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac303-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ac303-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac303-131">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ac303-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac303-132">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac303-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac303-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac303-133">See Also</span></span>  
 [<span data-ttu-id="ac303-134">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="ac303-134">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="ac303-135">Interface IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="ac303-135">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)