---
title: "Método IHostPolicyManager::OnDefaultAction"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostPolicyManager.OnDefaultAction
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostPolicyManager::OnDefaultAction
helpviewer_keywords:
- OnDefaultAction method [.NET Framework hosting]
- IHostPolicyManager::OnDefaultAction method [.NET Framework hosting]
ms.assetid: 071e73bd-4795-470f-9373-cfaef553b7f2
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca5eb767c08733980c9156d04526594c62349624
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="ac41f-102">Método IHostPolicyManager::OnDefaultAction</span><span class="sxs-lookup"><span data-stu-id="ac41f-102">IHostPolicyManager::OnDefaultAction Method</span></span>
<span data-ttu-id="ac41f-103">Notifica o host que o common language runtime (CLR) está prestes a realizar a ação padrão que foi definida por uma chamada para o [SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) método em resposta a uma anulação de thread ou <xref:System.AppDomain> descarregar.</span><span class="sxs-lookup"><span data-stu-id="ac41f-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac41f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac41f-104">Syntax</span></span>  
  
```  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ac41f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ac41f-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="ac41f-106">[in] Uma da [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) valores, que indica o tipo de evento para o qual o CLR está respondendo.</span><span class="sxs-lookup"><span data-stu-id="ac41f-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="ac41f-107">[in] Uma da [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valores, que indica a ação que o CLR está sendo em resposta ao evento.</span><span class="sxs-lookup"><span data-stu-id="ac41f-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac41f-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ac41f-108">Return Value</span></span>  
  
|<span data-ttu-id="ac41f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ac41f-109">HRESULT</span></span>|<span data-ttu-id="ac41f-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac41f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ac41f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ac41f-111">S_OK</span></span>|<span data-ttu-id="ac41f-112">`OnDefaultAction`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="ac41f-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="ac41f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ac41f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ac41f-114">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada.</span><span class="sxs-lookup"><span data-stu-id="ac41f-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="ac41f-115">com êxito</span><span class="sxs-lookup"><span data-stu-id="ac41f-115">successfully</span></span>|  
|<span data-ttu-id="ac41f-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ac41f-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ac41f-117">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="ac41f-117">The call timed out.</span></span>|  
|<span data-ttu-id="ac41f-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ac41f-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ac41f-119">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="ac41f-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ac41f-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ac41f-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ac41f-121">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="ac41f-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ac41f-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ac41f-122">E_FAIL</span></span>|<span data-ttu-id="ac41f-123">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="ac41f-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ac41f-124">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="ac41f-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ac41f-125">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ac41f-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ac41f-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ac41f-126">Requirements</span></span>  
 <span data-ttu-id="ac41f-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac41f-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac41f-128">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ac41f-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac41f-129">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ac41f-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac41f-130">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac41f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac41f-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac41f-131">See Also</span></span>  
 [<span data-ttu-id="ac41f-132">Enumeração EClrOperation</span><span class="sxs-lookup"><span data-stu-id="ac41f-132">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="ac41f-133">Enumeração EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="ac41f-133">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="ac41f-134">Interface ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="ac41f-134">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="ac41f-135">Interface IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="ac41f-135">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)