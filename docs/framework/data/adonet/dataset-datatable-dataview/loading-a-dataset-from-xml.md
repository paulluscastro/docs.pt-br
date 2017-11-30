---
title: Carregando um DataSet a partir de XML
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
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: db507bf4f90d875960408857c7e6b1e3aa145730
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="loading-a-dataset-from-xml"></a><span data-ttu-id="81311-102">Carregando um DataSet a partir de XML</span><span class="sxs-lookup"><span data-stu-id="81311-102">Loading a DataSet from XML</span></span>
<span data-ttu-id="81311-103">O conteúdo de um <xref:System.Data.DataSet> ADO.NET pode ser criado de um fluxo ou documento XML.</span><span class="sxs-lookup"><span data-stu-id="81311-103">The contents of an ADO.NET <xref:System.Data.DataSet> can be created from an XML stream or document.</span></span> <span data-ttu-id="81311-104">Além disso, com o .NET Framework, você tem grande flexibilidade sobre quais informações são carregadas do XML e como o esquema ou estrutura relacional do <xref:System.Data.DataSet> é criado.</span><span class="sxs-lookup"><span data-stu-id="81311-104">In addition, with the .NET Framework you have great flexibility over what information is loaded from XML, and how the schema or relational structure of the <xref:System.Data.DataSet> is created.</span></span>  
  
 <span data-ttu-id="81311-105">Para preencher um <xref:System.Data.DataSet> com dados de XML, use o **ReadXml** método o <xref:System.Data.DataSet> objeto.</span><span class="sxs-lookup"><span data-stu-id="81311-105">To fill a <xref:System.Data.DataSet> with data from XML, use the **ReadXml** method of the <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="81311-106">O **ReadXml** método lê de um arquivo, um fluxo ou um **XmlReader**e usa como argumentos a origem do XML mais um recurso opcional **XmlReadMode** argumento.</span><span class="sxs-lookup"><span data-stu-id="81311-106">The **ReadXml** method reads from a file, a stream, or an **XmlReader**, and takes as arguments the source of the XML plus an optional **XmlReadMode** argument.</span></span> <span data-ttu-id="81311-107">(Para obter mais informações sobre o **XmlReader**, consulte [NIB: leitura de dados XML com XmlTextReader](http://msdn.microsoft.com/en-us/762c069b-b50c-41b8-936e-39eacfb0d540).) O **ReadXml** método lê o conteúdo do fluxo XML ou documento e carrega o <xref:System.Data.DataSet> com dados.</span><span class="sxs-lookup"><span data-stu-id="81311-107">(For more information about the **XmlReader**, see [NIB: Reading XML Data with XmlTextReader](http://msdn.microsoft.com/en-us/762c069b-b50c-41b8-936e-39eacfb0d540).) The **ReadXml** method reads the contents of the XML stream or document and loads the <xref:System.Data.DataSet> with data.</span></span> <span data-ttu-id="81311-108">Também criará o esquema relacional do <xref:System.Data.DataSet> dependendo do **XmlReadMode** especificado e se já existe um esquema relacional.</span><span class="sxs-lookup"><span data-stu-id="81311-108">It will also create the relational schema of the <xref:System.Data.DataSet> depending on the **XmlReadMode** specified and whether or not a relational schema already exists.</span></span>  
  
 <span data-ttu-id="81311-109">A tabela a seguir descreve as opções para o **XmlReadMode** argumento.</span><span class="sxs-lookup"><span data-stu-id="81311-109">The following table describes the options for the **XmlReadMode** argument.</span></span>  
  
|<span data-ttu-id="81311-110">Opção</span><span class="sxs-lookup"><span data-stu-id="81311-110">Option</span></span>|<span data-ttu-id="81311-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="81311-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="81311-112">**Auto**</span><span class="sxs-lookup"><span data-stu-id="81311-112">**Auto**</span></span>|<span data-ttu-id="81311-113">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="81311-113">This is the default.</span></span> <span data-ttu-id="81311-114">Examina o XML e escolhe a opção mais apropriada na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="81311-114">Examines the XML and chooses the most appropriate option in the following order:</span></span><br /><br /> <span data-ttu-id="81311-115">-Se o XML é um DiffGram, **DiffGram** é usado.</span><span class="sxs-lookup"><span data-stu-id="81311-115">-   If the XML is a DiffGram, **DiffGram** is used.</span></span><br /><span data-ttu-id="81311-116">-Se a <xref:System.Data.DataSet> contém um esquema ou o XML contém um esquema embutido, **ReadSchema** é usado.</span><span class="sxs-lookup"><span data-stu-id="81311-116">-   If the <xref:System.Data.DataSet> contains a schema or the XML contains an inline schema, **ReadSchema** is used.</span></span><br /><span data-ttu-id="81311-117">-Se a <xref:System.Data.DataSet> não contém um esquema e o XML não contém um esquema embutido, **InferSchema** é usado.</span><span class="sxs-lookup"><span data-stu-id="81311-117">-   If the <xref:System.Data.DataSet> does not contain a schema and the XML does not contain an inline schema, **InferSchema** is used.</span></span><br /><br /> <span data-ttu-id="81311-118">Se você souber o formato do XML que está sendo lido, para melhor desempenho é recomendável que você defina uma explícita **XmlReadMode**, em vez de aceitar o **automática** padrão.</span><span class="sxs-lookup"><span data-stu-id="81311-118">If you know the format of the XML being read, for best performance it is recommended that you set an explicit **XmlReadMode**, rather than accept the **Auto** default.</span></span>|  
|<span data-ttu-id="81311-119">**ReadSchema**</span><span class="sxs-lookup"><span data-stu-id="81311-119">**ReadSchema**</span></span>|<span data-ttu-id="81311-120">Lê qualquer esquema embutido e carrega os dados e o esquema.</span><span class="sxs-lookup"><span data-stu-id="81311-120">Reads any inline schema and loads the data and schema.</span></span><br /><br /> <span data-ttu-id="81311-121">Se o <xref:System.Data.DataSet> já contiver um esquema, novas tabelas serão adicionadas do esquema embutido para o esquema existente no <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="81311-121">If the <xref:System.Data.DataSet> already contains a schema, new tables are added from the inline schema to the existing schema in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="81311-122">Se qualquer tabela no esquema embutido já existir no <xref:System.Data.DataSet>, uma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="81311-122">If any tables in the inline schema already exist in the <xref:System.Data.DataSet>, an exception is thrown.</span></span> <span data-ttu-id="81311-123">Você não poderá modificar o esquema de uma tabela existente usando **XmlReadMode.ReadSchema**.</span><span class="sxs-lookup"><span data-stu-id="81311-123">You will not be able to modify the schema of an existing table using **XmlReadMode.ReadSchema**.</span></span><br /><br /> <span data-ttu-id="81311-124">Se o <xref:System.Data.DataSet> não contiver um esquema, e não houver nenhum esquema embutido, nenhum dado será lido.</span><span class="sxs-lookup"><span data-stu-id="81311-124">If the <xref:System.Data.DataSet> does not contain a schema, and there is no inline schema, no data is read.</span></span><br /><br /> <span data-ttu-id="81311-125">O esquema embutido pode ser definido usando o esquema da linguagem XSD.</span><span class="sxs-lookup"><span data-stu-id="81311-125">Inline schema can be defined using XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="81311-126">Para obter detalhes sobre como escrever um esquema embutido como um esquema XML, consulte [derivando estrutura relacional do DataSet do esquema XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="81311-126">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>|  
|<span data-ttu-id="81311-127">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="81311-127">**IgnoreSchema**</span></span>|<span data-ttu-id="81311-128">Ignora qualquer esquema embutido e carrega os dados no esquema <xref:System.Data.DataSet> existente.</span><span class="sxs-lookup"><span data-stu-id="81311-128">Ignores any inline schema and loads the data into the existing <xref:System.Data.DataSet> schema.</span></span> <span data-ttu-id="81311-129">Os dados que não corresponderem ao esquema existente serão descartados.</span><span class="sxs-lookup"><span data-stu-id="81311-129">Any data that does not match the existing schema is discarded.</span></span> <span data-ttu-id="81311-130">Se nenhum esquema existir no <xref:System.Data.DataSet>, nenhum dado será carregado.</span><span class="sxs-lookup"><span data-stu-id="81311-130">If no schema exists in the <xref:System.Data.DataSet>, no data is loaded.</span></span><br /><br /> <span data-ttu-id="81311-131">Se os dados forem um DiffGram, **IgnoreSchema** tem a mesma funcionalidade que **DiffGram** *.*</span><span class="sxs-lookup"><span data-stu-id="81311-131">If the data is a DiffGram, **IgnoreSchema** has the same functionality as **DiffGram** *.*</span></span>|  
|<span data-ttu-id="81311-132">**InferSchema**</span><span class="sxs-lookup"><span data-stu-id="81311-132">**InferSchema**</span></span>|<span data-ttu-id="81311-133">Ignora qualquer esquema embutido e infere o esquema pela estrutura dos dados XML, para então carregar os dados.</span><span class="sxs-lookup"><span data-stu-id="81311-133">Ignores any inline schema and infers the schema per the structure of the XML data, then loads the data.</span></span><br /><br /> <span data-ttu-id="81311-134">Se o <xref:System.Data.DataSet> já contiver um esquema, o esquema atual será estendido adicionando colunas às tabelas existentes.</span><span class="sxs-lookup"><span data-stu-id="81311-134">If the <xref:System.Data.DataSet> already contains a schema, the current schema is extended by adding columns to existing tables.</span></span> <span data-ttu-id="81311-135">As tabelas adicionais não serão adicionadas se não houver tabelas existentes.</span><span class="sxs-lookup"><span data-stu-id="81311-135">Extra tables will not be added if there are not existing tables.</span></span> <span data-ttu-id="81311-136">Uma exceção será lançada se uma tabela inferida já existir com um namespace diferente, ou se qualquer coluna inferida estiver em conflito com colunas existentes.</span><span class="sxs-lookup"><span data-stu-id="81311-136">An exception is thrown if an inferred table already exists with a different namespace, or if any inferred columns conflict with existing columns.</span></span><br /><br /> <span data-ttu-id="81311-137">Para obter detalhes sobre como **ReadXmlSchema** infere um esquema de um documento XML, consulte [inferindo estrutura relacional do conjunto de dados do XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="81311-137">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span></span>|  
|<span data-ttu-id="81311-138">**DiffGram**</span><span class="sxs-lookup"><span data-stu-id="81311-138">**DiffGram**</span></span>|<span data-ttu-id="81311-139">Lê um DiffGram e adiciona os dados no esquema atual.</span><span class="sxs-lookup"><span data-stu-id="81311-139">Reads a DiffGram and adds the data to the current schema.</span></span> <span data-ttu-id="81311-140">**DiffGram** mescla linhas novas com linhas existentes onde correspondem as valores de identificador exclusivo.</span><span class="sxs-lookup"><span data-stu-id="81311-140">**DiffGram** merges new rows with existing rows where the unique identifier values match.</span></span> <span data-ttu-id="81311-141">Consulte "Mesclando dados de XML” no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="81311-141">See "Merging Data from XML" at the end of this topic.</span></span> <span data-ttu-id="81311-142">Para obter mais informações sobre DiffGrams, consulte [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span><span class="sxs-lookup"><span data-stu-id="81311-142">For more information about DiffGrams, see [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span></span>|  
|<span data-ttu-id="81311-143">**Fragmento**</span><span class="sxs-lookup"><span data-stu-id="81311-143">**Fragment**</span></span>|<span data-ttu-id="81311-144">Continua a ler múltiplos fragmentos XML até que o final do fluxo seja alcançado.</span><span class="sxs-lookup"><span data-stu-id="81311-144">Continues reading multiple XML fragments until the end of the stream is reached.</span></span> <span data-ttu-id="81311-145">Os fragmentos que corresponderem ao esquema <xref:System.Data.DataSet> são adicionados às tabelas apropriadas.</span><span class="sxs-lookup"><span data-stu-id="81311-145">Fragments that match the <xref:System.Data.DataSet> schema are appended to the appropriate tables.</span></span> <span data-ttu-id="81311-146">Os fragmentos que não corresponderem ao esquema <xref:System.Data.DataSet> serão descartados.</span><span class="sxs-lookup"><span data-stu-id="81311-146">Fragments that do not match the <xref:System.Data.DataSet> schema are discarded.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="81311-147">Se você passar um **XmlReader** para **ReadXml** que faz parte posicionada de maneira em um documento XML, **ReadXml** serão lidas para o próximo nó de elemento e tratá-lo como a raiz elemento, até o término do nó de elemento apenas de leitura.</span><span class="sxs-lookup"><span data-stu-id="81311-147">If you pass an **XmlReader** to **ReadXml** that is positioned part of the way into an XML document, **ReadXml** will read to the next element node and will treat that as the root element, reading until the end of the element node only.</span></span> <span data-ttu-id="81311-148">Isso não se aplica se você especificar **XmlReadMode**.</span><span class="sxs-lookup"><span data-stu-id="81311-148">This does not apply if you specify **XmlReadMode.Fragment**.</span></span>  
  
## <a name="dtd-entities"></a><span data-ttu-id="81311-149">Entidades DTD</span><span class="sxs-lookup"><span data-stu-id="81311-149">DTD Entities</span></span>  
 <span data-ttu-id="81311-150">Se o XML contém entidades definidas em um esquema DTD (definição) de tipo de documento, uma exceção será lançada se você tentar carregar um <xref:System.Data.DataSet> passando um arquivo de nome, fluxo ou não validar **XmlReader** para  **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="81311-150">If your XML contains entities defined in a document type definition (DTD) schema, an exception will be thrown if you attempt to load a <xref:System.Data.DataSet> by passing a file name, stream, or non-validating **XmlReader** to **ReadXml**.</span></span> <span data-ttu-id="81311-151">Em vez disso, você deve criar um **XmlValidatingReader**, com **EntityHandling** definida como **ExpandEntities**e passe o  **XmlValidatingReader** para **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="81311-151">Instead, you must create an **XmlValidatingReader**, with **EntityHandling** set to **EntityHandling.ExpandEntities**, and pass your **XmlValidatingReader** to **ReadXml**.</span></span> <span data-ttu-id="81311-152">O **XmlValidatingReader** expandirá as entidades antes de serem lidos pelo <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="81311-152">The **XmlValidatingReader** will expand the entities prior to being read by the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="81311-153">Os seguintes exemplos de código mostram como carregar um <xref:System.Data.DataSet> de um fluxo XML.</span><span class="sxs-lookup"><span data-stu-id="81311-153">The following code examples show how to load a <xref:System.Data.DataSet> from an XML stream.</span></span> <span data-ttu-id="81311-154">O primeiro exemplo mostra um nome de arquivo que está sendo passado para o **ReadXml** método.</span><span class="sxs-lookup"><span data-stu-id="81311-154">The first example shows a file name being passed to the **ReadXml** method.</span></span> <span data-ttu-id="81311-155">O segundo exemplo mostra uma cadeia de caracteres que contém o XML que está sendo carregado usando um <xref:System.IO.StringReader>.</span><span class="sxs-lookup"><span data-stu-id="81311-155">The second example shows a string that contains XML being loaded using a <xref:System.IO.StringReader>.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema);  
```  
  
```vb  
Dim dataSet As DataSet = New DataSet  
Dim dataTable As DataTable = New DataTable("table1")  
dataTable.Columns.Add("col1", Type.GetType("System.String"))  
dataSet.Tables.Add(dataTable)  
  
Dim xmlData As String = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>"  
  
Dim xmlSR As System.IO.StringReader = New System.IO.StringReader(xmlData)  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
DataTable dataTable = new DataTable("table1");  
dataTable.Columns.Add("col1", typeof(string));  
dataSet.Tables.Add(dataTable);  
  
string xmlData = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>";  
  
System.IO.StringReader xmlSR = new System.IO.StringReader(xmlData);  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema);  
```  
  
> [!NOTE]
>  <span data-ttu-id="81311-156">Se você chamar **ReadXml** para carregar um arquivo muito grande, você pode encontrar um desempenho lento.</span><span class="sxs-lookup"><span data-stu-id="81311-156">If you call **ReadXml** to load a very large file, you may encounter slow performance.</span></span> <span data-ttu-id="81311-157">Para garantir o melhor desempenho para **ReadXml**, em um arquivo grande, chame o <xref:System.Data.DataTable.BeginLoadData%2A> método para cada tabela no <xref:System.Data.DataSet>e, em seguida, chame **ReadXml**.</span><span class="sxs-lookup"><span data-stu-id="81311-157">To ensure best performance for **ReadXml**, on a large file, call the <xref:System.Data.DataTable.BeginLoadData%2A> method for each table in the <xref:System.Data.DataSet>, and then call **ReadXml**.</span></span> <span data-ttu-id="81311-158">Finalmente, chame <xref:System.Data.DataTable.EndLoadData%2A> para cada tabela no <xref:System.Data.DataSet>, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="81311-158">Finally, call <xref:System.Data.DataTable.EndLoadData%2A> for each table in the <xref:System.Data.DataSet>, as shown in the following example.</span></span>  
  
```vb  
Dim dataTable As DataTable  
  
For Each dataTable In dataSet.Tables  
   dataTable.BeginLoadData()  
Next  
  
dataSet.ReadXml("file.xml")  
  
For Each dataTable in dataSet.Tables  
   dataTable.EndLoadData()  
Next  
```  
  
```csharp  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.BeginLoadData();  
  
dataSet.ReadXml("file.xml");   
  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.EndLoadData();  
```  
  
> [!NOTE]
>  <span data-ttu-id="81311-159">Se o esquema XSD para o <xref:System.Data.DataSet> inclui um **targetNamespace**, os dados não podem ser lidos e você poderá encontrar exceções, ao chamar **ReadXml** para carregar o <xref:System.Data.DataSet> com XML que contém elementos sem namespace qualificado.</span><span class="sxs-lookup"><span data-stu-id="81311-159">If the XSD schema for your <xref:System.Data.DataSet> includes a **targetNamespace**, data may not be read, and you may encounter exceptions, when calling **ReadXml** to load the <xref:System.Data.DataSet> with XML that contains elements with no qualifying namespace.</span></span> <span data-ttu-id="81311-160">Para ler os elementos não qualificados, nesse caso, defina **elementFormDefault** igual a "qualificado" em seu esquema XSD.</span><span class="sxs-lookup"><span data-stu-id="81311-160">To read unqualified elements in this case, set **elementFormDefault** equal to "qualified" in your XSD schema.</span></span> <span data-ttu-id="81311-161">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="81311-161">For example:</span></span>  
  
```xml  
<xsd:schema id="customDataSet"   
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"   
  xmlns="http://www.tempuri.org/customDataSet.xsd"   
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a><span data-ttu-id="81311-162">Mesclando dados de XML</span><span class="sxs-lookup"><span data-stu-id="81311-162">Merging Data from XML</span></span>  
 <span data-ttu-id="81311-163">Se o <xref:System.Data.DataSet> já contiver dados, os novos dados XML serão adicionados aos dados já presentes no <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="81311-163">If the <xref:System.Data.DataSet> already contains data, the new data from the XML is added to the data already present in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="81311-164">**ReadXml** não mescla do XML para o <xref:System.Data.DataSet> qualquer linha de informações com correspondência de chaves primárias.</span><span class="sxs-lookup"><span data-stu-id="81311-164">**ReadXml** does not merge from the XML into the <xref:System.Data.DataSet> any row information with matching primary keys.</span></span> <span data-ttu-id="81311-165">Para substituir as informações de linha existentes com novas informações de XML, use **ReadXml** para criar um novo <xref:System.Data.DataSet>e, em seguida, <xref:System.Data.DataSet.Merge%2A> novo <xref:System.Data.DataSet> em existente <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="81311-165">To overwrite existing row information with new information from XML, use **ReadXml** to create a new <xref:System.Data.DataSet>, and then <xref:System.Data.DataSet.Merge%2A> the new <xref:System.Data.DataSet> into the existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="81311-166">Observe que carregar um DiffGram usando **ReadXML** com um **XmlReadMode** de **DiffGram** mesclará as linhas que têm o mesmo identificador exclusivo.</span><span class="sxs-lookup"><span data-stu-id="81311-166">Note that loading a DiffGram using **ReadXML** with an **XmlReadMode** of **DiffGram** will merge rows that have the same unique identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81311-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81311-167">See Also</span></span>  
 <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>  
 <span data-ttu-id="81311-168">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="81311-168">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)</span></span>  
 [<span data-ttu-id="81311-169">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="81311-169">DiffGrams</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 [<span data-ttu-id="81311-170">Derivando a estrutura relacional do conjunto de dados de esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="81311-170">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [<span data-ttu-id="81311-171">Inferindo estrutura relacional do conjunto de dados do XML</span><span class="sxs-lookup"><span data-stu-id="81311-171">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="81311-172">Carregando informações de esquema de conjunto de dados de XML</span><span class="sxs-lookup"><span data-stu-id="81311-172">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 <span data-ttu-id="81311-173">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="81311-173">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>  
 <span data-ttu-id="81311-174">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="81311-174">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>