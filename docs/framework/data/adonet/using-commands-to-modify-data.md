---
title: Usando os comandos para modificar dados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 70a83453eef990a03515a4860917f3c4d72599c3
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="using-commands-to-modify-data"></a>Usando os comandos para modificar dados
Usando um provedor de dados do .NET Framework, você pode executar os procedimentos armazenados ou instruções definição de dados idioma (por exemplo, CREATE TABLE e ALTER COLUMN) para executar a manipulação de esquema em um banco de dados ou catálogo. Esses comandos não retornam linhas como uma consulta, portanto, o **comando** objeto fornece um **ExecuteNonQuery** para processá-las.  
  
 Além de usar **ExecuteNonQuery** para modificar o esquema, você também pode usar esse método para instruções SQL de processo que modificam dados, mas que não retornam linhas, como INSERT, UPDATE e excluir.  
  
 Embora linhas não são retornadas pelo **ExecuteNonQuery** parâmetros de método de entrada e saída e valores de retorno podem ser passados e retornados por meio de **parâmetros** coleção do **comando**  objeto.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Atualizando dados em uma fonte de dados](../../../../docs/framework/data/adonet/updating-data-in-a-data-source.md)  
 Descreve como executar comandos ou procedimentos armazenados que modificam dados em um banco de dados.  
  
 [Executando operações de catálogo](../../../../docs/framework/data/adonet/performing-catalog-operations.md)  
 Descreve como executar comandos que modificam o esquema de banco de dados.  
  
## <a name="see-also"></a>Consulte também  
 [Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)  
 [Comandos e parâmetros](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
