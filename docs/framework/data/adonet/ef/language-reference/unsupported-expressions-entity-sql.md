---
title: "Expressões sem suporte (Entity SQL)"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-ado
ms.topic: article
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
dev_langs:
- sql
ms.openlocfilehash: 075daf0e4f0477dda50231760fbb3d990a9f8468
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2018
---
# <a name="unsupported-expressions"></a>Não há suporte para expressões

Este tópico descreve [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressões que não têm suporte em [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Para obter mais informações, consulte [como o Entity SQL difere do Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).

## <a name="quantified-predicates"></a>Predicados quantificados

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] permite que as construções da seguinte forma:

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)], no entanto, não oferece suporte a tais construções. As expressões equivalentes podem ser gravadas em [!INCLUDE[esql](../../../../../../includes/esql-md.md)] como segue:

```sql
not exists(select 0 from employees as e where sal > e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a>Operador *

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] oferece suporte ao uso do * operador na cláusula SELECT para indicar que todas as colunas devem ser projetadas. Isso não é suportado em [!INCLUDE[esql](../../../../../../includes/esql-md.md)].

## <a name="see-also"></a>Consulte também

[Visão geral do Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
[Diferenças entre o Entity SQL e o Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
