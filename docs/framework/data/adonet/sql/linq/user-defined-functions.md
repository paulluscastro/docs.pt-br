---
title: Funções definidas pelo usuário
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 2e015b8fff16ade9bbe93e5e036c53d5527b961f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="user-defined-functions"></a>Funções definidas pelo usuário
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] usa métodos no seu modelo de objeto para representar funções definidas pelo usuário. Você designa métodos como funções aplicando o atributo de <xref:System.Data.Linq.Mapping.FunctionAttribute> e, quando for necessário, o atributo de <xref:System.Data.Linq.Mapping.ParameterAttribute> . Para obter mais informações, consulte [o LINQ no modelo de objeto do SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
 Para evitar <xref:System.InvalidOperationException>, funções definidas pelo usuário em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] devem estar em um das seguintes formas:  
  
-   Uma função empacotada como um chamada de método que tem os atributos corretos de mapeamento. Para obter mais informações, consulte [mapeamento baseado no atributo](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
-   Um específico do método SQL estático a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
-   Uma função suportada por um método de [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] .  
  
 Os tópicos nesta seção de apresentação como formar e chamar esses métodos em seu aplicativo se você escreve o código que você mesmo. Os desenvolvedores usando o Visual Studio normalmente usaria o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para mapear as funções definidas pelo usuário.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como usar as funções definidas pelo usuário com valor escalar](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-scalar-valued-user-defined-functions.md)  
 Descreve como implementar uma função que retorna valores escalares.  
  
 [Como usar as funções definidas pelo usuário com valor de tabela](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-table-valued-user-defined-functions.md)  
 Descreve como implementar uma função que retorna apresentam valores.  
  
 [Como chamar funções definidas pelo usuário embutido](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)  
 Descreve como fazer chamadas a funções embutidas e as diferenças em execução quando o chamada é feita embutido.
