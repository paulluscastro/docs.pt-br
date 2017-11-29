---
title: "Função QualifierSet_Delete (referência de API não gerenciada)"
description: "A função QualifierSet_Delete exclui um qualificador por nome."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_Delete
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_Delete
helpviewer_keywords: QualifierSet_Delete function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9245fc0ee109837249f1f3df400385c117a2f2d7
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="qualifiersetdelete-function"></a><span data-ttu-id="7b772-103">Função QualifierSet_Delete</span><span class="sxs-lookup"><span data-stu-id="7b772-103">QualifierSet_Delete function</span></span>
<span data-ttu-id="7b772-104">Exclui um qualificador especificado por nome.</span><span class="sxs-lookup"><span data-stu-id="7b772-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="7b772-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7b772-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a><span data-ttu-id="7b772-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7b772-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="7b772-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="7b772-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="7b772-108">[in] Um ponteiro para um [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instância.</span><span class="sxs-lookup"><span data-stu-id="7b772-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`wszName`   
<span data-ttu-id="7b772-109">[in] O nome do qualificador para excluir.</span><span class="sxs-lookup"><span data-stu-id="7b772-109">[in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="7b772-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="7b772-110">Return value</span></span>

<span data-ttu-id="7b772-111">Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="7b772-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="7b772-112">Constante</span><span class="sxs-lookup"><span data-stu-id="7b772-112">Constant</span></span>  |<span data-ttu-id="7b772-113">Valor</span><span class="sxs-lookup"><span data-stu-id="7b772-113">Value</span></span>  |<span data-ttu-id="7b772-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="7b772-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="7b772-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="7b772-115">0x80041008</span></span> | <span data-ttu-id="7b772-116">O parâmetro `wszName` não é válido.</span><span class="sxs-lookup"><span data-stu-id="7b772-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="7b772-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="7b772-117">0x80041016</span></span> | <span data-ttu-id="7b772-118">Excluir este qualificador é inválido.</span><span class="sxs-lookup"><span data-stu-id="7b772-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="7b772-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="7b772-119">0x80041002</span></span> | <span data-ttu-id="7b772-120">O qualificador especificado não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="7b772-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="7b772-121">0</span><span class="sxs-lookup"><span data-stu-id="7b772-121">0</span></span> | <span data-ttu-id="7b772-122">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="7b772-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="7b772-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="7b772-123">0x40002</span></span> | <span data-ttu-id="7b772-124">A substituição local foi excluída e o qualificador original do objeto pai retomou o escopo.</span><span class="sxs-lookup"><span data-stu-id="7b772-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="7b772-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="7b772-125">Remarks</span></span>

<span data-ttu-id="7b772-126">Essa função encapsula uma chamada para o [IWbemQualifierSet::Delete](https://msdn.microsoft.com/library/aa391864(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="7b772-126">This function wraps a call to the [IWbemQualifierSet::Delete](https://msdn.microsoft.com/library/aa391864(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="7b772-127">Devido a regras de propagação de qualificador, um qualificador específico foi herdado de outro objeto e simplesmente substituído na classe atual ou instância.</span><span class="sxs-lookup"><span data-stu-id="7b772-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="7b772-128">Nesse caso, o `QualifierSet_Delete` método redefine o qualificador para seu valor original de herdadas.</span><span class="sxs-lookup"><span data-stu-id="7b772-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="7b772-129">Nesse caso, a função retorna o código de status `WBEM_S_RESET_TO_DEFAULT`.</span><span class="sxs-lookup"><span data-stu-id="7b772-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="7b772-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7b772-130">Requirements</span></span>  
 <span data-ttu-id="7b772-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b772-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b772-132">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="7b772-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="7b772-133">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7b772-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b772-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b772-134">See also</span></span>  
[<span data-ttu-id="7b772-135">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="7b772-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)