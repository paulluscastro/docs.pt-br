---
title: Dados FILESTREAM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2fde543187d1904da93be255878d6c7a99de6bbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="filestream-data"></a><span data-ttu-id="8a9c1-102">Dados FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="8a9c1-102">FILESTREAM Data</span></span>
<span data-ttu-id="8a9c1-103">O atributo de armazenamento FILESTREAM é usado para dados binários BLOB armazenados em uma coluna varbinary(max).</span><span class="sxs-lookup"><span data-stu-id="8a9c1-103">The FILESTREAM storage attribute is for binary (BLOB) data stored in a varbinary(max) column.</span></span> <span data-ttu-id="8a9c1-104">Antes do FILESTREAM, armazenar dados binários exigia procedimentos especiais.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-104">Before FILESTREAM, storing binary data required special handling.</span></span> <span data-ttu-id="8a9c1-105">Os dados não estruturados, como documentos de texto, imagens e vídeo, geralmente são armazenados fora do banco de dados, o que os torna difíceis de serem gerenciados.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-105">Unstructured data, such as text documents, images and video, is often stored outside of the database, making it difficult to manage.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a9c1-106">Você deve instalar o .NET Framework 3.5 SP1 (ou posterior) para trabalhar com dados FILESTREAM usando o SqlClient.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-106">You must install the .NET Framework 3.5 SP1 (or later) to work with FILESTREAM data using SqlClient.</span></span>  
  
 <span data-ttu-id="8a9c1-107">A especificação do atributo FILESTREAM em uma coluna varbinary(max) faz com que o [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] armazene os dados no sistema de arquivos NTFS local em vez de no arquivo de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-107">Specifying the FILESTREAM attribute on a varbinary(max) column causes [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] to store the data on the local NTFS file system instead of in the database file.</span></span> <span data-ttu-id="8a9c1-108">Embora eles sejam armazenados separadamente, você pode usar as mesmas instruções [!INCLUDE[tsql](../../../../../includes/tsql-md.md)], que são suportadas para trabalhar com dados varbinary(max) que estão armazenados no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-108">Although it is stored separately, you can use the same [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statements that are supported for working with varbinary(max) data that is stored in the database.</span></span>  
  
## <a name="sqlclient-support-for-filestream"></a><span data-ttu-id="8a9c1-109">Suporte do SqlClient para FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="8a9c1-109">SqlClient Support for FILESTREAM</span></span>  
 <span data-ttu-id="8a9c1-110">O Provedor de Dados [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] para [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)], <xref:System.Data.SqlClient>, dá suporte à leitura e à gravação em dados FILESTREAM usando a classe <xref:System.Data.SqlTypes.SqlFileStream> definida no namespace <xref:System.Data.SqlTypes>.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-110">The [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Data Provider for [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)], <xref:System.Data.SqlClient>, supports reading and writing to FILESTREAM data using the <xref:System.Data.SqlTypes.SqlFileStream> class defined in the <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="8a9c1-111">O `SqlFileStream` herda da classe <xref:System.IO.Stream>, que fornece métodos para a leitura e a gravação em fluxos de dados.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-111">`SqlFileStream` inherits from the <xref:System.IO.Stream> class, which provides methods for reading and writing to streams of data.</span></span> <span data-ttu-id="8a9c1-112">A leitura de um fluxo transfere os dados do fluxo para uma estrutura de dados, como uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-112">Reading from a stream transfers data from the stream into a data structure, such as an array of bytes.</span></span> <span data-ttu-id="8a9c1-113">A gravação transfere os dados da estrutura de dados para um fluxo.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-113">Writing transfers the data from the data structure into a stream.</span></span>  
  
### <a name="creating-the-includessnoversionincludesssnoversion-mdmd-table"></a><span data-ttu-id="8a9c1-114">Criando a tabela [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a9c1-114">Creating the [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Table</span></span>  
 <span data-ttu-id="8a9c1-115">As instruções [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] a seguir criam uma tabela denominada employees e insere uma linha de dados.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-115">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statements creates a table named employees and inserts a row of data.</span></span> <span data-ttu-id="8a9c1-116">Depois de habilitar o armazenamento FILESTREAM, você pode usar essa tabela em conjunto com os exemplos de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-116">Once you have enabled FILESTREAM storage, you can use this table in conjunction with the code examples that follow.</span></span> <span data-ttu-id="8a9c1-117">Os links para os recursos nos Manuais Online do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-117">The links to resources in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online are located at the end of this topic.</span></span>  
  
```  
CREATE TABLE employees  
(  
  EmployeeId INT  NOT NULL  PRIMARY KEY,  
  Photo VARBINARY(MAX) FILESTREAM  NULL,  
  RowGuid UNIQUEIDENTIFIER  NOT NULL  ROWGUIDCOL  
  UNIQUE DEFAULT NEWID()  
)  
GO  
Insert into employees  
Values(1, 0x00, default)  
GO  
```  
  
### <a name="example-reading-overwriting-and-inserting-filestream-data"></a><span data-ttu-id="8a9c1-118">Exemplo: ler, substituindo e inserir dados FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="8a9c1-118">Example: Reading, Overwriting, and Inserting FILESTREAM Data</span></span>  
 <span data-ttu-id="8a9c1-119">O exemplo a seguir demonstra como ler dados de um FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-119">The following sample demonstrates how to read data from a FILESTREAM.</span></span> <span data-ttu-id="8a9c1-120">O código obtém o caminho lógico do arquivo, definindo `FileAccess` como `Read` e `FileOptions` como `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-120">The code gets the logical path to the file, setting the `FileAccess` to `Read` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="8a9c1-121">Em seguida, o código lê os bytes do SqlFileStream no buffer.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-121">The code then reads the bytes from the SqlFileStream into the buffer.</span></span> <span data-ttu-id="8a9c1-122">Os bytes são então gravados na janela do console.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-122">The bytes are then written to the console window.</span></span>  
  
 <span data-ttu-id="8a9c1-123">O exemplo também demonstra como gravar dados em um FILESTREAM em que todos os dados existentes são substituídos.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-123">The sample also demonstrates how to write data to a FILESTREAM in which all existing data is overwritten.</span></span> <span data-ttu-id="8a9c1-124">O código obtém o caminho lógico do arquivo e cria o `SqlFileStream`, definindo `FileAccess` como `Write` e `FileOptions` como `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-124">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `Write` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="8a9c1-125">Um único byte é gravado no `SqlFileStream`, substituindo todos os dados do arquivo.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-125">A single byte is written to the `SqlFileStream`, replacing any data in the file.</span></span>  
  
 <span data-ttu-id="8a9c1-126">O exemplo também demonstra como gravar dados em um FILESTREAM usando o método Seek para acrescentar dados ao final do arquivo.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-126">The sample also demonstrates how to write data to a FILESTREAM by using the Seek method to append data to the end of the file.</span></span> <span data-ttu-id="8a9c1-127">O código obtém o caminho lógico do arquivo e cria o `SqlFileStream`, definindo `FileAccess` como `ReadWrite` e `FileOptions` como `SequentialScan`.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-127">The code gets the logical path to the file and creates the `SqlFileStream`, setting the `FileAccess` to `ReadWrite` and the `FileOptions` to `SequentialScan`.</span></span> <span data-ttu-id="8a9c1-128">O código usa o método Seek para buscar o final do arquivo, acrescentando um único byte ao arquivo existente.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-128">The code uses the Seek method to seek to the end of the file, appending a single byte to the existing file.</span></span>  
  
```csharp  
using System;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Data;  
using System.IO;  
  
namespace FileStreamTest  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder("server=(local);integrated security=true;database=myDB");  
            ReadFilestream(builder);  
            OverwriteFilestream(builder);  
            InsertFilestream(builder);  
  
            Console.WriteLine("Done");  
        }  
  
        private static void ReadFilestream(SqlConnectionStringBuilder connStringBuilder)  
        {  
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))  
            {  
                connection.Open();  
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);  
  
                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);  
                command.Transaction = tran;  
  
                using (SqlDataReader reader = command.ExecuteReader())  
                {  
                    while (reader.Read())  
                    {  
                        // Get the pointer for the file  
                        string path = reader.GetString(0);  
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
                        // Create the SqlFileStream  
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Read, FileOptions.SequentialScan, allocationSize: 0))  
                        {  
                            // Read the contents as bytes and write them to the console  
                            for (long index = 0; index < fileStream.Length; index++)  
                            {  
                                Console.WriteLine(fileStream.ReadByte());  
                            }  
                        }  
                    }  
                }  
                tran.Commit();  
            }  
        }  
  
        private static void OverwriteFilestream(SqlConnectionStringBuilder connStringBuilder)  
        {  
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))  
            {  
                connection.Open();  
  
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);  
  
                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);  
                command.Transaction = tran;  
  
                using (SqlDataReader reader = command.ExecuteReader())  
                {  
                    while (reader.Read())  
                    {  
                        // Get the pointer for file   
                        string path = reader.GetString(0);  
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
                        // Create the SqlFileStream  
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Write, FileOptions.SequentialScan, allocationSize: 0))  
                        {  
                            // Write a single byte to the file. This will  
                            // replace any data in the file.  
                            fileStream.WriteByte(0x01);  
                        }  
                    }  
                }  
                tran.Commit();  
            }  
        }  
  
        private static void InsertFilestream(SqlConnectionStringBuilder connStringBuilder)  
        {  
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))  
            {  
                connection.Open();  
  
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);  
  
                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);  
                command.Transaction = tran;  
  
                using (SqlDataReader reader = command.ExecuteReader())  
                {  
                    while (reader.Read())  
                    {  
                        // Get the pointer for file  
                        string path = reader.GetString(0);  
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Write, FileOptions.SequentialScan, allocationSize: 0))  
                        {  
                            // Seek to the end of the file  
                            fileStream.Seek(0, SeekOrigin.End);  
  
                            // Append a single byte   
                            fileStream.WriteByte(0x01);  
                        }  
                    }  
                }  
                tran.Commit();  
            }  
  
        }  
    }  
} using (SqlConnection connection = new SqlConnection(  
    connStringBuilder.ToString()))  
{  
    connection.Open();  
  
    SqlCommand command = new SqlCommand("", connection);  
    command.CommandText = "select Top(1) Photo.PathName(), "  
    + "GET_FILESTREAM_TRANSACTION_CONTEXT () from employees";  
  
    SqlTransaction tran = connection.BeginTransaction(  
        System.Data.IsolationLevel.ReadCommitted);  
    command.Transaction = tran;  
  
    using (SqlDataReader reader = command.ExecuteReader())  
    {  
        while (reader.Read())  
        {  
            // Get the pointer for file  
            string path = reader.GetString(0);  
            byte[] transactionContext = reader.GetSqlBytes(1).Buffer;  
  
            FileStream fileStream = new SqlFileStream(path,  
                (byte[])reader.GetValue(1),  
                FileAccess.ReadWrite,  
                FileOptions.SequentialScan, 0);  
  
            // Seek to the end of the file  
            fs.Seek(0, SeekOrigin.End);  
  
            // Append a single byte   
            fileStream.WriteByte(0x01);  
            fileStream.Close();  
        }  
    }  
    tran.Commit();  
}  
```  
  
 <span data-ttu-id="8a9c1-129">Para obter outro exemplo, consulte [como armazenar e buscar os dados binários em uma coluna de fluxo de arquivo](http://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span><span class="sxs-lookup"><span data-stu-id="8a9c1-129">For another sample, see [How to store and fetch binary data into a file stream column](http://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).</span></span>  
  
## <a name="resources-in-includessnoversionincludesssnoversion-mdmd-books-online"></a><span data-ttu-id="8a9c1-130">Recursos nos Manuais Online do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a9c1-130">Resources in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online</span></span>  
 <span data-ttu-id="8a9c1-131">A documentação completa do FILESTREAM está localizada nas seguintes seções dos Manuais Online do [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8a9c1-131">The complete documentation for FILESTREAM is located in the following sections in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
|<span data-ttu-id="8a9c1-132">Tópico</span><span class="sxs-lookup"><span data-stu-id="8a9c1-132">Topic</span></span>|<span data-ttu-id="8a9c1-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a9c1-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8a9c1-134">[Projetando e implementando armazenamento FILESTREAM](http://msdn2.microsoft.com/library/bb895234\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="8a9c1-134">[Designing and Implementing FILESTREAM Storage](http://msdn2.microsoft.com/library/bb895234\(SQL.105\).aspx)</span></span>|<span data-ttu-id="8a9c1-135">Fornece links para a documentação do FILESTREAM e para os tópicos relacionados.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-135">Provides links to FILESTREAM documentation and related topics.</span></span>|  
|<span data-ttu-id="8a9c1-136">[Visão geral de FILESTREAM](http://msdn2.microsoft.com/library/bb933993\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="8a9c1-136">[FILESTREAM Overview](http://msdn2.microsoft.com/library/bb933993\(SQL.105\).aspx)</span></span>|<span data-ttu-id="8a9c1-137">Descreve quando usar o armazenamento FILESTREAM e como ele se integra com o Mecanismo de Banco de Dados do SQL Server com um sistema de arquivos NTFS.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-137">Describes when to use FILESTREAM storage and how it integrates the SQL Server Database Engine with an NTFS file system.</span></span>|  
|<span data-ttu-id="8a9c1-138">[Guia de Introdução ao armazenamento de FILESTREAM](http://msdn.microsoft.com/library/bb933995\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="8a9c1-138">[Getting Started with FILESTREAM Storage](http://msdn.microsoft.com/library/bb933995\(SQL.105\).aspx)</span></span>|<span data-ttu-id="8a9c1-139">Descreve como habilitar o FILESTREAM em uma instância do SQL Server, como criar um banco de dados e uma tabela para dados FILESTREAM armazenados e como manipular as linhas que contêm dados FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-139">Describes how to enable FILESTREAM on an instance of SQL Server, how to create a database and a table to stored FILESTREAM data, and how to manipulate rows containing FILESTREAM data.</span></span>|  
|<span data-ttu-id="8a9c1-140">[Usando o armazenamento FILESTREAM em aplicativos cliente](http://msdn.microsoft.com/library/bb933877\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="8a9c1-140">[Using FILESTREAM Storage in Client Applications](http://msdn.microsoft.com/library/bb933877\(SQL.105\).aspx)</span></span>|<span data-ttu-id="8a9c1-141">Descreve as funções da API do Win32 para trabalhar com dados FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-141">Describes the Win32 API functions for working with FILESTREAM data.</span></span>|  
|<span data-ttu-id="8a9c1-142">[FILESTREAM e outros recursos do SQL Server](http://msdn.microsoft.com/library/bb895334\(SQL.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="8a9c1-142">[FILESTREAM and Other SQL Server Features](http://msdn.microsoft.com/library/bb895334\(SQL.105\).aspx)</span></span>|<span data-ttu-id="8a9c1-143">Fornece considerações, diretrizes e limitações para usar dados FILESTREAM com outros recursos do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8a9c1-143">Provides considerations, guidelines and limitations for using FILESTREAM data with other features of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8a9c1-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a9c1-144">See Also</span></span>  
 <span data-ttu-id="8a9c1-145">[SQL Server Data Types and ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md) (Tipos de dados do SQL Server e o ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="8a9c1-145">[SQL Server Data Types and ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)</span></span>  
 <span data-ttu-id="8a9c1-146">[Retrieving and Modifying Data in ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="8a9c1-146">[Retrieving and Modifying Data in ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)</span></span>  
 [<span data-ttu-id="8a9c1-147">Segurança de acesso do código e o ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8a9c1-147">Code Access Security and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/code-access-security.md)  
 <span data-ttu-id="8a9c1-148">[SQL Server Binary and Large-Value Data](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md) (Dados binários e de valor grande do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="8a9c1-148">[SQL Server Binary and Large-Value Data](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)</span></span>  
 <span data-ttu-id="8a9c1-149">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="8a9c1-149">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>