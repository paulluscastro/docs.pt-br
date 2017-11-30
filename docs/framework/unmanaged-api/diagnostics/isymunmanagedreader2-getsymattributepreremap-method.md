---
title: "Método ISymUnmanagedReader2::GetSymAttributePreRemap"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader2.GetSymAttributePreRemap
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 75608d89b6fd34570166718de824150b0621c84e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a><span data-ttu-id="49c71-102">Método ISymUnmanagedReader2::GetSymAttributePreRemap</span><span class="sxs-lookup"><span data-stu-id="49c71-102">ISymUnmanagedReader2::GetSymAttributePreRemap Method</span></span>
<span data-ttu-id="49c71-103">Obtém um atributo personalizado com base no seu nome.</span><span class="sxs-lookup"><span data-stu-id="49c71-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="49c71-104">Ao contrário de atributos personalizados de metadados, esses atributos são mantidos no repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="49c71-104">Unlike metadata custom attributes, these attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49c71-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="49c71-105">Syntax</span></span>  
  
```  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="49c71-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="49c71-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="49c71-107">[in] O token de metadados do pai.</span><span class="sxs-lookup"><span data-stu-id="49c71-107">[in] The metadata token of the parent.</span></span>  
  
 `name`  
 <span data-ttu-id="49c71-108">[in] Um ponteiro para um `WCHAR` que contém o nome.</span><span class="sxs-lookup"><span data-stu-id="49c71-108">[in] A pointer to a `WCHAR` that contains the name.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="49c71-109">[in] Um `ULONG32` que indica o tamanho do `buffer` matriz.</span><span class="sxs-lookup"><span data-stu-id="49c71-109">[in] A `ULONG32` that indicates the size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="49c71-110">[out] Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os bytes de atributo.</span><span class="sxs-lookup"><span data-stu-id="49c71-110">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the attribute bytes.</span></span>  
  
 `buffer`  
 <span data-ttu-id="49c71-111">[out] Um ponteiro para o buffer que recebe os bytes de atributo.</span><span class="sxs-lookup"><span data-stu-id="49c71-111">[out] A pointer to the buffer that receives the attribute bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49c71-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="49c71-112">Return Value</span></span>  
 <span data-ttu-id="49c71-113">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="49c71-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49c71-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="49c71-114">Requirements</span></span>  
 <span data-ttu-id="49c71-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="49c71-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49c71-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49c71-116">See Also</span></span>  
 [<span data-ttu-id="49c71-117">Interface ISymUnmanagedReader2</span><span class="sxs-lookup"><span data-stu-id="49c71-117">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)