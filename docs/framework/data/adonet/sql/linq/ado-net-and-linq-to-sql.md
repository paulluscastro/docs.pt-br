---
title: O ADO.NET e LINQ to SQL
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
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c95a84bafcb32861e299135feb0b89b931d11165
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="adonet-and-linq-to-sql"></a>O ADO.NET e LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]é parte do [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] família de tecnologias. É baseada em serviços fornecidos pelo modelo de provedor de [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] . Portanto, você pode misturar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] código com existente [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] aplicativos e migrar atual [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] soluções para [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. A ilustração a seguir fornece uma exibição de alto nível de relacionamento.  
  
 ![LINQ to SQL e o ADO.NET](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinq-3.png "DLinq_3")  
  
## <a name="connections"></a>Conexões  
 Você pode fornecer um existente [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] conexão quando você cria um [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>. Todas as operações em relação a <xref:System.Data.Linq.DataContext> (incluindo consultas) use fornecido a conexão. Se a conexão já estiver aberto, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] deixar como está quando tiver terminado com ele.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 Você sempre pode acessar a conexão e fechá-lo você mesmo usando a propriedade de <xref:System.Data.Linq.DataContext.Connection%2A> , como no código a seguir:  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a>Transações  
 Você pode fornecer seu <xref:System.Data.Linq.DataContext> com sua própria transação de base de dados quando seu aplicativo é iniciado na transação e você deseja que o <xref:System.Data.Linq.DataContext> a ser empacotado.  
  
 O método preferido de transações fazer com [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] é usar o objeto de <xref:System.Transactions.TransactionScope> . Usando essa abordagem, você pode fazer as transações distribuídas que funcionam através de bases de dados e outros gerentes de recurso de memória residente. Escopos de transação requerem alguns recursos para começar. Eles se autopromover a transações distribuídas somente quando há várias conexões dentro do escopo da transação.  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 Você não pode usar essa abordagem para todos os bases de dados. Por exemplo, a conexão SqlClient não pode elevar transações do sistema quando trabalha em um servidor de [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] . Em vez disso, inscreve-se automaticamente para uma transação completa, distribuído consulta sempre que um escopo de transação que está sendo usado.  
  
## <a name="direct-sql-commands"></a>Comandos SQL diretos  
 Às vezes você pode encontrar situações onde a capacidade de <xref:System.Data.Linq.DataContext> de consulte ou enviar alterações insuficientes para a tarefa específica que você deseja executar. Nesteas circunstâncias você pode usar o método de <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> para emitir comandos SQL a base de dados e para converter os resultados da consulta a objetos.  
  
 Por exemplo, suponha que os dados para a classe de `Customer` são espalhado sobre duas tabelas (customer1 e customer2). A seguinte consulta retorna uma sequência de objetos `Customer` :  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 Como os nomes de coluna nos resultados da tabela correspondem a propriedades de coluna de sua classe de entidade, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cria os objetos fora de qualquer consulta SQL.  
  
### <a name="parameters"></a>Parâmetros  
 O método de <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> aceita parâmetros. O código a seguir executa uma consulta parametrizada:  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
>  Os parâmetros são expressos no texto da consulta usando a mesma notação encaracolado usada por `Console.WriteLine()` e por `String.Format()`. `String.Format()` leva a cadeia de caracteres de consulta que você fornece e substitui os parâmetros encaracolado- apoiados com nomes de parâmetro gerados como `@p0`, `@p1` …, `@p(n)`.  
  
## <a name="see-also"></a>Consulte também  
 [Informações gerais](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Como reutilizar uma conexão entre um comando ADO.NET e um DataContext](../../../../../../docs/framework/data/adonet/sql/linq/how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
