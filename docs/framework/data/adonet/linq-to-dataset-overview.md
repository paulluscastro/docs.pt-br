---
title: LINQ para visão geral do DataSet
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 3e030ca62625e2b8870cf0eeb5694f4b889b3a7e
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="linq-to-dataset-overview"></a>LINQ para visão geral do DataSet
O <xref:System.Data.DataSet> é um dos componentes mais amplamente usados de [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. É um elemento fundamental do desconectada modelo de programação que [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] se baseia, e permite que você explicitamente os dados em cache de fontes de dados diferentes. Para a camada de apresentação, o <xref:System.Data.DataSet> é integrado com controles de interface gráfica do usuário para associação de dados. Para a camada intermediária, ele fornece um cache que preserva a forma relacional de dados e inclui a consulta rápida simples e serviços de navegação de hierarquia. Uma técnica comum usada para reduzir o número de solicitações em um banco de dados é usar o <xref:System.Data.DataSet> para armazenar em cache na camada intermediária. Por exemplo, considere um controlada por dados [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo Web. Geralmente, uma parte significativa de dados do aplicativo não muda com frequência e é comum em sessões ou usuários. Esses dados podem ser mantidos na memória no servidor Web, reduzindo o número de solicitações no banco de dados e acelerando as interações do usuário. Outro aspecto útil de <xref:System.Data.DataSet> é que ele permite que um aplicativo para colocar subconjuntos de dados de um ou mais fonte de dados no espaço do aplicativo. O aplicativo pode manipular os dados na memória, mantendo sua forma relacional.  
  
 Apesar de sua importância, o <xref:System.Data.DataSet> limitou os recursos de consulta. O método <xref:System.Data.DataTable.Select%2A> pode ser usado para filtrar e classificar, e os métodos <xref:System.Data.DataRow.GetChildRows%2A> e <xref:System.Data.DataRow.GetParentRow%2A> podem ser usados para navegação a hierarquia. Para algo mais complexo, no entanto, o desenvolvedor precisa escrever uma consulta personalizada. Isso pode resultar em aplicativos com baixo desempenho e de difícil manutenção.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] torna mais fácil e rápido a consulta sobre os dados armazenados em cache uma <xref:System.Data.DataSet> objeto. Essas consultas são expressas na própria linguagem de programação, e não como os literais de cadeia de caracteres inseridos no código do aplicativo. Isso significa que os desenvolvedores não precisam aprender uma linguagem de consulta separada. Além disso, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] permite que os desenvolvedores do Visual Studio trabalhar produtivamente, porque o IDE do Visual Studio fornece verificação de sintaxe de tempo de compilação, digitação estática e suporte ao IntelliSense para [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]. O [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] também pode ser usado para efetuar consultas a dados que foram consolidados de uma ou mais fontes de dados. Isso habilita vários cenários que exigem flexibilidade na maneira como dados são representados e tratados. Em particular, relatórios genéricos, análise e aplicativos de business intelligence exigem esse método de manipulação.  
  
## <a name="querying-datasets-using-linq-to-dataset"></a>Consultando DataSets usando o LINQ to DataSet  
 Antes de começar a consultar um <xref:System.Data.DataSet> objeto usando [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], você deve preencher o <xref:System.Data.DataSet>. Há várias maneiras para carregar dados em um <xref:System.Data.DataSet>, como usar o <xref:System.Data.Common.DataAdapter> classe ou [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md). Depois que os dados foram carregados em um <xref:System.Data.DataSet> do objeto, você pode começar a consultá-los. Formular consultas usando [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] é semelhante ao uso de [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] contra outros [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-habilitado fontes de dados. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] consultas podem ser executadas em relação a tabelas único em uma <xref:System.Data.DataSet> ou em mais de uma tabela usando o <xref:System.Linq.Enumerable.Join%2A> e <xref:System.Linq.Enumerable.GroupJoin%2A> operadores de consulta padrão.  
  
 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] as consultas têm suporte em ambos e sem-tipo <xref:System.Data.DataSet> objetos. Se o esquema do <xref:System.Data.DataSet> é conhecido em tempo de design de aplicativo, com um tipo <xref:System.Data.DataSet> é recomendado. Em um tipo <xref:System.Data.DataSet>, as tabelas e linhas digitou membros para cada uma das colunas, o que torna as consultas mais simples e mais legível.  
  
 Além dos operadores de consulta padrão implementados no System.Core.dll, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] adiciona várias <xref:System.Data.DataSet>-extensões específicas que facilitam a consulta em um conjunto de <xref:System.Data.DataRow> objetos. Essas extensões específicas de <xref:System.Data.DataSet> incluem operadores para comparar sequências de linhas, bem como métodos que fornecem acesso aos valores de coluna de <xref:System.Data.DataRow>.  
  
## <a name="n-tier-applications-and-linq-to-dataset"></a>Aplicativos de n camadas e LINQ to DataSet  
 Aplicativos de dados de n camadas são aplicativos centrados em dados que são separados em várias camadas lógicas (ou camadas). Um aplicativo de n camadas típico inclui uma camada de apresentação, uma camada intermediária e uma camada de dados. Dividir componentes do aplicativo em camadas separadas aumenta a facilidade de manutenção e a escalabilidade do aplicativo. Para obter mais informações sobre aplicativos de N camadas de dados, consulte [trabalhar com conjuntos de dados em aplicativos de n camadas](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20).  
  
 Em aplicativos de n camadas, o <xref:System.Data.DataSet> costuma ser usado na camada intermediária para armazenar em cache informações para um aplicativo Web. O [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] consultando a funcionalidade é implementada por meio de métodos de extensão e estende o ADO.NET 2.0 existente <xref:System.Data.DataSet>.  
  
## <a name="see-also"></a>Consulte também  
 [Consultando DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [LINQ (Consulta Integrada à Linguagem)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)
