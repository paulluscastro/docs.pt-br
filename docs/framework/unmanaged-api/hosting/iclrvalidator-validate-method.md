---
title: "Método ICLRValidator::Validate"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::Validate
helpviewer_keywords:
- Validate method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::Validate method [.NET Framework hosting]
ms.assetid: 0b1b432a-d234-4002-839b-81366c3a8bdc
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7328fe62276de6c33464ab8cfc6d6a5f39ee710e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrvalidatorvalidate-method"></a>Método ICLRValidator::Validate
Valida o PE (executável portátil) ou Microsoft intermediate language (MSIL) no arquivo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Validate (  
    [in] IVEHandler        *veh,  
    [in] unsigned long      ulAppDomainId,  
    [in] unsigned long      ulFlags,  
    [in] unsigned long      ulMaxError,  
    [in] unsigned long      token,  
    [in] LPWSTR             fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long      ulSize  
);      
```  
  
#### <a name="parameters"></a>Parâmetros  
 `veh`  
 [in] Um ponteiro para um `IVEHandler` instância que manipula erros de validação.  
  
 `ulAppDomainId`  
 [in] O identificador para a <xref:System.AppDomain>.  
  
 `ulFlags`  
 [in] Uma combinação de [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) valores, que indica o tipo de validação deve ser executada.  
  
 `ulMaxError`  
 [in] O número máximo de erros permitido antes de sair da validação.  
  
 `token`  
 [in] Não usado.  
  
 `fileName`  
 [in] O nome do arquivo a ser validado.  
  
 `pe`  
 [in] Um ponteiro para o buffer de arquivo.  
  
 `ulSize`  
 [in] O tamanho, em bytes, do arquivo a ser validado.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`Validate`retornou com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada foi atingido.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo. As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** IValidator.idl, IValidator.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRValidator](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
