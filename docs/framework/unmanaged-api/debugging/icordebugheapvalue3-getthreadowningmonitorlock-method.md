---
title: "Método ICorDebugHeapValue3::GetThreadOwningMonitorLock"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3571f546f71515a980c5415e568ae85eb0863d42
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="9c7a5-102">Método ICorDebugHeapValue3::GetThreadOwningMonitorLock</span><span class="sxs-lookup"><span data-stu-id="9c7a5-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>
<span data-ttu-id="9c7a5-103">Retorna o thread gerenciado que possui o bloqueio de monitor nesse objeto.</span><span class="sxs-lookup"><span data-stu-id="9c7a5-103">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c7a5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9c7a5-104">Syntax</span></span>  
  
```  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c7a5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9c7a5-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="9c7a5-106">[out] O thread gerenciado que possui o bloqueio de monitor nesse objeto.</span><span class="sxs-lookup"><span data-stu-id="9c7a5-106">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="9c7a5-107">[out] O número de vezes que esse thread precisa liberar o bloqueio antes de retornar para sendo sem proprietário.</span><span class="sxs-lookup"><span data-stu-id="9c7a5-107">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c7a5-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9c7a5-108">Return Value</span></span>  
 <span data-ttu-id="9c7a5-109">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="9c7a5-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9c7a5-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9c7a5-110">HRESULT</span></span>|<span data-ttu-id="9c7a5-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c7a5-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9c7a5-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="9c7a5-112">S_OK</span></span>|<span data-ttu-id="9c7a5-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="9c7a5-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="9c7a5-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9c7a5-114">S_FALSE</span></span>|<span data-ttu-id="9c7a5-115">Nenhum thread gerenciado possui o bloqueio de monitor nesse objeto.</span><span class="sxs-lookup"><span data-stu-id="9c7a5-115">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="9c7a5-116">Exceções</span><span class="sxs-lookup"><span data-stu-id="9c7a5-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c7a5-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="9c7a5-117">Remarks</span></span>  
 <span data-ttu-id="9c7a5-118">Se um thread gerenciado possui o bloqueio de monitor nesse objeto:</span><span class="sxs-lookup"><span data-stu-id="9c7a5-118">If a managed thread owns the monitor lock on this object:</span></span>  
  
-   <span data-ttu-id="9c7a5-119">O método retorna S_OK.</span><span class="sxs-lookup"><span data-stu-id="9c7a5-119">The method returns S_OK.</span></span>  
  
-   <span data-ttu-id="9c7a5-120">O objeto de thread é válido até que o thread será encerrado.</span><span class="sxs-lookup"><span data-stu-id="9c7a5-120">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="9c7a5-121">Se nenhum thread gerenciado possui o bloqueio de monitor nesse objeto `ppThread` e `pAcquisitionCount` foram modificados, e o método retornará S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="9c7a5-121">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="9c7a5-122">Se `ppThread` ou `pAcquisitionCount` não é um ponteiro válido, o resultado é indefinido.</span><span class="sxs-lookup"><span data-stu-id="9c7a5-122">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="9c7a5-123">Se ocorrer um erro, de modo que ele não pode ser determinado que, se houver, thread possui o bloqueio de monitor nesse objeto, o método retorna um HRESULT que indica falha.</span><span class="sxs-lookup"><span data-stu-id="9c7a5-123">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c7a5-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9c7a5-124">Requirements</span></span>  
 <span data-ttu-id="9c7a5-125">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c7a5-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c7a5-126">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c7a5-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c7a5-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c7a5-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c7a5-128">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c7a5-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c7a5-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c7a5-129">See Also</span></span>  
 [<span data-ttu-id="9c7a5-130">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="9c7a5-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9c7a5-131">Depuração</span><span class="sxs-lookup"><span data-stu-id="9c7a5-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)