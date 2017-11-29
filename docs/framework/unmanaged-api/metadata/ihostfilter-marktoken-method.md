---
title: "Método IHostFilter::MarkToken"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostFilter.MarkToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostFilter::MarkToken
helpviewer_keywords:
- MarkToken method, IHostFilter interface [.NET Framework metadata]
- IHostFilter::MarkToken method [.NET Framework metadata]
ms.assetid: d7061343-d0a3-4fd5-b312-61974f98bd62
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9556880ad534f5c82d8d0e874129876478e2e63f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="b96df-102">Método IHostFilter::MarkToken</span><span class="sxs-lookup"><span data-stu-id="b96df-102">IHostFilter::MarkToken Method</span></span>
<span data-ttu-id="b96df-103">Indica que o token de metadados especificado será processado.</span><span class="sxs-lookup"><span data-stu-id="b96df-103">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b96df-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b96df-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b96df-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b96df-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="b96df-106">[in] O token de metadados a serem processadas.</span><span class="sxs-lookup"><span data-stu-id="b96df-106">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b96df-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b96df-107">Remarks</span></span>  
 <span data-ttu-id="b96df-108">Geralmente, você deseja um token a ser processada se ele está no escopo de metadados.</span><span class="sxs-lookup"><span data-stu-id="b96df-108">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="b96df-109">O `MarkToken` método é passado para o mecanismo de metadados por meio de [: Sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="b96df-109">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b96df-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b96df-110">Requirements</span></span>  
 <span data-ttu-id="b96df-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b96df-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b96df-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b96df-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b96df-113">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b96df-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b96df-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b96df-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b96df-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b96df-115">See Also</span></span>  
 [<span data-ttu-id="b96df-116">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="b96df-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="b96df-117">Interface IHostFilter</span><span class="sxs-lookup"><span data-stu-id="b96df-117">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)