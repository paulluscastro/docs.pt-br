---
title: "Método ICorProfilerInfo4::EnumJITedFunctions2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.EnumJITedFunctions2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::EnumJITedFunctions2
helpviewer_keywords:
- EnumJITedFunctions2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::EnumJITedFunctions2 method [.NET Framework profiling]
ms.assetid: 40e9a1be-9bd2-4fad-9921-34a84b61c1e3
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9b9c8739a8ab47b4e24dba1b15c228d2800290d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a><span data-ttu-id="44eb1-102">Método ICorProfilerInfo4::EnumJITedFunctions2</span><span class="sxs-lookup"><span data-stu-id="44eb1-102">ICorProfilerInfo4::EnumJITedFunctions2 Method</span></span>
<span data-ttu-id="44eb1-103">Retorna um enumerador para todas as funções que foram anteriormente compilados JIT e recompilado JIT.</span><span class="sxs-lookup"><span data-stu-id="44eb1-103">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span> <span data-ttu-id="44eb1-104">Esse método substitui o [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) método, que não enumerar IDs recompilado JIT.</span><span class="sxs-lookup"><span data-stu-id="44eb1-104">This method replaces the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) method, which does not enumerate JIT-recompiled IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44eb1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44eb1-105">Syntax</span></span>  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="44eb1-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="44eb1-106">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="44eb1-107">[out] Um ponteiro para o [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerador.</span><span class="sxs-lookup"><span data-stu-id="44eb1-107">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44eb1-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="44eb1-108">Remarks</span></span>  
 <span data-ttu-id="44eb1-109">Esse método pode sobrepor `JITCompilation` retornos de chamada, como o [: Jitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="44eb1-109">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="44eb1-110">A enumeração retornada inclui valores para o `COR_PRF_FUNCTION::reJitId` campo.</span><span class="sxs-lookup"><span data-stu-id="44eb1-110">The returned enumeration includes values for the `COR_PRF_FUNCTION::reJitId` field.</span></span> <span data-ttu-id="44eb1-111">O [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) método, que substitui esse método, não enumerar recompilado JIT IDs, porque o `COR_PRF_FUNCTION::reJitId` campo é sempre definido como 0.</span><span class="sxs-lookup"><span data-stu-id="44eb1-111">The [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) method, which this method replaces, does not enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is always set to 0.</span></span> <span data-ttu-id="44eb1-112">O `ICorProfilerInfo4::EnumJITedFunctions` método enumerar recompilado JIT IDs, porque o `COR_PRF_FUNCTION::reJitId` campo está definido corretamente.</span><span class="sxs-lookup"><span data-stu-id="44eb1-112">The `ICorProfilerInfo4::EnumJITedFunctions` method does enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is set properly.</span></span> <span data-ttu-id="44eb1-113">Observe que o [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) métodos pode disparar uma coleta de lixo, enquanto [ICorProfilerInfo3::EnumJITedFunctions método](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) não.</span><span class="sxs-lookup"><span data-stu-id="44eb1-113">Note that the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method can trigger a garbage collection, whereas [ICorProfilerInfo3::EnumJITedFunctions method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) will not.</span></span>  <span data-ttu-id="44eb1-114">Para obter mais informações, consulte [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="44eb1-114">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44eb1-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="44eb1-115">Requirements</span></span>  
 <span data-ttu-id="44eb1-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44eb1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44eb1-117">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="44eb1-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="44eb1-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44eb1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44eb1-119">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44eb1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44eb1-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44eb1-120">See Also</span></span>  
 [<span data-ttu-id="44eb1-121">Método EnumJITedFunctions</span><span class="sxs-lookup"><span data-stu-id="44eb1-121">EnumJITedFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)  
 [<span data-ttu-id="44eb1-122">Interface ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="44eb1-122">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="44eb1-123">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="44eb1-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="44eb1-124">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="44eb1-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)