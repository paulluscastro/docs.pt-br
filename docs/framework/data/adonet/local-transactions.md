---
title: Transações locais
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8ae3712f-ef5e-41a1-9ea9-b3d0399439f1
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: d56e2a978c3b9b58eadb946ee053721435c9f2d9
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="local-transactions"></a>Transações locais
As transações no [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] são usadas quando o usuário deseja associar várias tarefas para que possam ser executadas como uma unidade de trabalho. Por exemplo, imagine que um aplicativo executa duas tarefas. Primeiro, ele atualiza uma tabela com informações sobre pedidos. Em seguida, ele atualiza uma tabela que contém informações de inventário, debitando os itens pedidos. Se a tarefa falhar, em seguida, ambas as atualizações serão revertidas.  
  
## <a name="determining-the-transaction-type"></a>Determinando o tipo de transação  
 Uma transação é considerada uma transação local quando ele é uma transação de fase única e é tratado pelo banco de dados diretamente. Uma transação é considerada uma transação distribuída quando ele é coordenado pelo monitor de uma transação e usa mecanismos à prova de falhas (como a confirmação de duas fases) para resolução de transações.  
  
 Cada provedor de dados do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tem seu próprio objeto `Transaction` para executar transações locais. Se você precisar executar uma transação em um banco de dados do SQL Server, selecione uma transação <xref:System.Data.SqlClient>. Para uma transação Oracle, use o provedor <xref:System.Data.OracleClient>. Além disso, há um <xref:System.Data.Common.DbTransaction> classe que está disponível para escrever código independente de provedor que requer transações.  
  
> [!NOTE]
>  As transações são mais eficientes quando executadas no servidor. Se você estiver trabalhando com um banco de dados do SQL Server que faz uso extensivo de transações explícitas, considere criá-las como procedimentos armazenados usando a instrução Transact-SQL BEGIN TRANSACTION. Para obter mais informações sobre como executar transações no servidor, consulte Manuais Online do SQL Server.  
  
## <a name="performing-a-transaction-using-a-single-connection"></a>Executando uma transação com uma única conexão  
 No [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], você controla transações com o objeto `Connection`. É possível iniciar uma transação local com o método `BeginTransaction`. Depois de iniciar uma transação, você pode inscrever um comando nessa transação com a propriedade `Transaction` de um objeto `Command`. Em seguida, você poderá confirmar ou reverter todas as modificações feitas na fonte de dados com base no êxito ou na falha dos componentes de transação.  
  
> [!NOTE]
>  O método `EnlistDistributedTransaction` não deve ser usado para uma transação local.  
  
 O escopo da transação é limitado à conexão. O exemplo a seguir executa uma transação explícita que consiste em dois comandos separados no bloco `try`. Os comandos executados instruções INSERT em relação à tabela scrapreason no banco de dados de exemplo AdventureWorks do SQL Server, que serão confirmadas se nenhuma exceção for lançada. O código no bloco `catch` reverte a transação se uma exceção é gerada. Se a transação for anulada ou a conexão for fechada antes de a transação ser concluída, a transação será automaticamente revertida.  
  
## <a name="example"></a>Exemplo  
 Siga estas etapas para executar uma transação.  
  
1.  Chame o método <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> do objeto <xref:System.Data.SqlClient.SqlConnection> para marcar o início da transação. O método <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> retorna uma referência à transação. Essa referência é atribuída aos objetos <xref:System.Data.SqlClient.SqlCommand> inscritos na transação.  
  
2.  Atribua o objeto `Transaction` à propriedade <xref:System.Data.SqlClient.SqlCommand.Transaction%2A> de <xref:System.Data.SqlClient.SqlCommand> a ser executado. Se um comando for executado em uma conexão com uma transação ativa, e o objeto `Transaction` não tiver sido atribuído à propriedade `Transaction` do objeto `Command`, uma exceção será gerada.  
  
3.  Execute os comandos necessários.  
  
4.  Chame o método <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> do objeto <xref:System.Data.SqlClient.SqlTransaction> para concluir a transação, ou chame o método <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> para finalizar a transação. Se a conexão for fechada ou descartada antes do método <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> ou <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> ser executado, a transação será revertida.  
  
 O exemplo de código a seguir demonstra a lógica transacional usando o [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] com o Microsoft SQL Server.  
  
 [!code-csharp[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/VB/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Transações e simultaneidade](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [Transações distribuídas](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 [Integração de System.Transactions com o SQL Server](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
