---
title: "Método ICorProfilerCallback::ModuleAttachedToAssembly"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ModuleAttachedToAssembly
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2c285a42bb48970756a54d5313d2839c76a9835c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a><span data-ttu-id="55808-102">Método ICorProfilerCallback::ModuleAttachedToAssembly</span><span class="sxs-lookup"><span data-stu-id="55808-102">ICorProfilerCallback::ModuleAttachedToAssembly Method</span></span>
<span data-ttu-id="55808-103">Notifica o criador de perfil que um módulo está sendo anexado ao seu assembly pai.</span><span class="sxs-lookup"><span data-stu-id="55808-103">Notifies the profiler that a module is being attached to its parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55808-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="55808-104">Syntax</span></span>  
  
```  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="55808-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="55808-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="55808-106">[in] A ID do módulo que está sendo anexado.</span><span class="sxs-lookup"><span data-stu-id="55808-106">[in] The ID of the module that is being attached.</span></span>  
  
 `AssemblyId`  
 <span data-ttu-id="55808-107">[in] A ID do assembly pai ao qual o módulo está anexado.</span><span class="sxs-lookup"><span data-stu-id="55808-107">[in] The ID of the parent assembly to which the module is attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55808-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="55808-108">Remarks</span></span>  
 <span data-ttu-id="55808-109">Um módulo pode ser carregado por meio de uma tabela de endereço de importação (IAT), por meio de uma chamada para `LoadLibrary`, ou por meio de uma referência de metadados.</span><span class="sxs-lookup"><span data-stu-id="55808-109">A module can be loaded through an import address table (IAT), through a call to `LoadLibrary`, or through a metadata reference.</span></span> <span data-ttu-id="55808-110">Como resultado, o carregador de runtime (CLR) de linguagem comum tem vários caminhos de código para determinar o assembly no qual existe um módulo.</span><span class="sxs-lookup"><span data-stu-id="55808-110">As a result, the common language runtime (CLR) loader has multiple code paths for determining the assembly in which a module lives.</span></span> <span data-ttu-id="55808-111">Portanto, é possível que, depois [: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) é chamado, o módulo não sabe qual assembly está em e não é possível obter a ID do assembly pai.</span><span class="sxs-lookup"><span data-stu-id="55808-111">Therefore, it is possible that after [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) is called, the module does not know what assembly it is in and getting the parent assembly ID is not possible.</span></span> <span data-ttu-id="55808-112">O `ModuleAttachedToAssembly` método é chamado quando o módulo está conectado ao seu assembly de pai e seu pai ID pode ser obtido.</span><span class="sxs-lookup"><span data-stu-id="55808-112">The `ModuleAttachedToAssembly` method is called when the module is attached to its parent assembly and its parent assembly ID can be obtained.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55808-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="55808-113">Requirements</span></span>  
 <span data-ttu-id="55808-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55808-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55808-115">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="55808-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="55808-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55808-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55808-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55808-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55808-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55808-118">See Also</span></span>  
 [<span data-ttu-id="55808-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="55808-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)