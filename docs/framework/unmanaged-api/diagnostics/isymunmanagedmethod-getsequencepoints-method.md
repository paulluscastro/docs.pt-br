---
title: "Método ISymUnmanagedMethod::GetSequencePoints"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetSequencePoints
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3cde9de634534acdeafa40bd7a94c46624e49604
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a><span data-ttu-id="29b0a-102">Método ISymUnmanagedMethod::GetSequencePoints</span><span class="sxs-lookup"><span data-stu-id="29b0a-102">ISymUnmanagedMethod::GetSequencePoints Method</span></span>
<span data-ttu-id="29b0a-103">Obtém todos os pontos de sequência dentro desse método.</span><span class="sxs-lookup"><span data-stu-id="29b0a-103">Gets all the sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29b0a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29b0a-104">Syntax</span></span>  
  
```  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29b0a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="29b0a-105">Parameters</span></span>  
 `cPoints`  
 <span data-ttu-id="29b0a-106">[in] Um `ULONG32` que recebe o tamanho do `offsets`, `documents`, `lines`, `columns`, `endLines`, e `endColumns` matrizes.</span><span class="sxs-lookup"><span data-stu-id="29b0a-106">[in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.</span></span>  
  
 `pcPoints`  
 <span data-ttu-id="29b0a-107">[out] Um ponteiro para um `ULONG32` que recebe o comprimento do buffer necessário para conter os pontos de sequência.</span><span class="sxs-lookup"><span data-stu-id="29b0a-107">[out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.</span></span>  
  
 `offsets`  
 <span data-ttu-id="29b0a-108">[in] Uma matriz na qual deseja armazenar o Microsoft intermediate language (MSIL) desloca desde o início do método para os pontos de sequência.</span><span class="sxs-lookup"><span data-stu-id="29b0a-108">[in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.</span></span>  
  
 `documents`  
 <span data-ttu-id="29b0a-109">[in] Uma matriz na qual deseja armazenar os documentos em que os pontos de sequência estão localizados.</span><span class="sxs-lookup"><span data-stu-id="29b0a-109">[in] An array in which to store the documents in which the sequence points are located.</span></span>  
  
 `lines`  
 <span data-ttu-id="29b0a-110">[in] Uma matriz na qual deseja armazenar as linhas nos documentos em que os pontos de sequência estão localizados.</span><span class="sxs-lookup"><span data-stu-id="29b0a-110">[in] An array in which to store the lines in the documents at which the sequence points are located.</span></span>  
  
 `columns`  
 <span data-ttu-id="29b0a-111">[in] Uma matriz na qual deseja armazenar as colunas nos documentos em que os pontos de sequência estão localizados.</span><span class="sxs-lookup"><span data-stu-id="29b0a-111">[in] An array in which to store the columns in the documents at which the sequence points are located.</span></span>  
  
 `endLines`  
 <span data-ttu-id="29b0a-112">[in] A matriz de linhas nos documentos em que a sequência de pontos finais.</span><span class="sxs-lookup"><span data-stu-id="29b0a-112">[in] The array of lines in the documents at which the sequence points end.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="29b0a-113">[in] A matriz de colunas nos documentos em que a sequência de pontos finais.</span><span class="sxs-lookup"><span data-stu-id="29b0a-113">[in] The array of columns in the documents at which the sequence points end.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29b0a-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="29b0a-114">Return Value</span></span>  
 <span data-ttu-id="29b0a-115">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="29b0a-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29b0a-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="29b0a-116">Requirements</span></span>  
 <span data-ttu-id="29b0a-117">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="29b0a-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29b0a-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29b0a-118">See Also</span></span>  
 [<span data-ttu-id="29b0a-119">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="29b0a-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)