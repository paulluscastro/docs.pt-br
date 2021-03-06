---
title: Comparando valores de GUID e uniqueidentifier
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: aababd75-2335-43e3-ace8-4b7ae84191a8
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0a61556859acec53315147149d67ff4cef493b68
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="comparing-guid-and-uniqueidentifier-values"></a>Comparando valores de GUID e uniqueidentifier
O tipo de dados de GUID (identificador exclusivo) no SQL Server é representado pelo tipo de dados `uniqueidentifier`, que armazena um valor binário de 16 bytes. O GUID é um número binário, e seu uso principal é como um identificador que deve ser exclusivo em uma rede que tenha muitos computadores em muitos sites. Os GUIDs podem ser gerados chamando a função Transact-SQL NEWID e têm a garantia de serem exclusivos em todo o mundo. Para obter mais informações, consulte "Usando dados uniqueidentifier" nos Manuais Online do SQL Server.  
  
## <a name="working-with-sqlguid-values"></a>Trabalhando com valores SqlGuid  
 Como são longos e obscuros, os valores de GUIDs não são significativos para os usuários. Se os GUIDs gerados aleatoriamente forem usados para valores de chave e você inserir várias linhas, obterá E/S aleatória em seus índices, o que pode afetar negativamente o desempenho. Os GUIDs também são relativamente grandes em comparação com outros tipos de dados. Em geral, recomendamos usar GUIDs apenas em cenários muito limitados para os quais nenhum outro tipo de dados é adequado.  
  
### <a name="comparing-guid-values"></a>Comparando valores de GUID  
 Operadores de comparação podem ser usados com valores `uniqueidentifier`. No entanto, a classificação não é implementada comparando os padrões de bits dos dois valores. As únicas operações que são permitidas em um `uniqueidentifier` valor são comparações (=, <>, \<, >, \<=, > =) e a verificação de NULL (IS NULL e IS NOT NULL). Nenhum outro operador aritmético é permitido.  
  
 <xref:System.Guid> e <xref:System.Data.SqlTypes.SqlGuid> têm um método `CompareTo` para comparar valores de GUIDs diferentes. No entanto, `System.Guid.CompareTo` e `SqlTypes.SqlGuid.CompareTo` são implementados de forma diferente. <xref:System.Data.SqlTypes.SqlGuid> implementa `CompareTo` usando o comportamento do SQL Server, no qual apenas os últimos seis bytes de um valor são mais significativos. <xref:System.Guid> avalia todos os 16 bytes. O exemplo a seguir demonstra essa diferença comportamental. A primeira seção do código exibe valores <xref:System.Guid> não classificados, e a segunda seção do código mostra os valores <xref:System.Guid> classificados. A terceira seção mostra os valores <xref:System.Data.SqlTypes.SqlGuid> classificados. A saída é exibida abaixo da listagem do código.  
  
 [!code-csharp[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/VB/source.vb#1)]  
  
 Esse exemplo produz os seguintes resultados:  
  
```  
Unsorted Guids:  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
  
Sorted Guids:  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
  
Sorted SqlGuids:  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
```  
  
## <a name="see-also"></a>Consulte também  
 [SQL Server Data Types and ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md) (Tipos de dados do SQL Server e o ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
