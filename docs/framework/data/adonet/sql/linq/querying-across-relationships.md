---
title: "Consulte através das relações"
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
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a347818818fe7c6e15535fd0c2c24548c52e57d5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="querying-across-relationships"></a><span data-ttu-id="7f850-102">Consulte através das relações</span><span class="sxs-lookup"><span data-stu-id="7f850-102">Querying Across Relationships</span></span>
<span data-ttu-id="7f850-103">Referências a outros objetos ou coleções de outros objetos em suas definições de classe correspondem diretamente às relações de chave estrangeira na base de dados.</span><span class="sxs-lookup"><span data-stu-id="7f850-103">References to other objects or collections of other objects in your class definitions directly correspond to foreign-key relationships in the database.</span></span> <span data-ttu-id="7f850-104">Você pode usar estas relações quando você consulta usando notação de ponto para acessar as propriedades de relação e para navegar de um objeto para outro.</span><span class="sxs-lookup"><span data-stu-id="7f850-104">You can use these relationships when you query by using dot notation to access the relationship properties and navigate from one object to another.</span></span> <span data-ttu-id="7f850-105">Essas operações de acesso a traduzem mais complexo join ou correlacionaram a subconsultas no equivalente SQL.</span><span class="sxs-lookup"><span data-stu-id="7f850-105">These access operations translate to more complex joins or correlated subqueries in the equivalent SQL.</span></span>  
  
 <span data-ttu-id="7f850-106">Por exemplo, a consulta a seguir navega pedidos para clientes como uma maneira de restringir os resultados apenas 2 os pedidos de clientes localizados em Londres.</span><span class="sxs-lookup"><span data-stu-id="7f850-106">For example, the following query navigates from orders to customers as a way to restrict the results to only those orders for customers located in London.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#3)]
 [!code-vb[DLinqQueryConcepts#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#3)]  
  
 <span data-ttu-id="7f850-107">Se as propriedades de relação não existe, você teria escrevê-los manualmente como *junções*, assim como você faria em uma consulta SQL, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="7f850-107">If relationship properties did not exist you would have to write them manually as *joins*, just as you would do in a SQL query, as in the following code:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#4)]
 [!code-vb[DLinqQueryConcepts#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#4)]  
  
 <span data-ttu-id="7f850-108">Você pode usar o *relação* propriedade para definir esta relação específica de uma vez.</span><span class="sxs-lookup"><span data-stu-id="7f850-108">You can use the *relationship* property to define this particular relationship one time.</span></span> <span data-ttu-id="7f850-109">Você pode usar a sintaxe mais conveniente de ponto.</span><span class="sxs-lookup"><span data-stu-id="7f850-109">You can then use the more convenient dot syntax.</span></span> <span data-ttu-id="7f850-110">Mas as propriedades de relação existem mais importante porque os modelos de objeto domínio específicos geralmente são definidos como hierarquias ou elementos gráficos.</span><span class="sxs-lookup"><span data-stu-id="7f850-110">But relationship properties exist more importantly because domain-specific object models are typically defined as hierarchies or graphs.</span></span> <span data-ttu-id="7f850-111">Os objetos que você programou com têm referências a outros objetos.</span><span class="sxs-lookup"><span data-stu-id="7f850-111">The objects that you program against have references to other objects.</span></span> <span data-ttu-id="7f850-112">É apenas uma coincidência felizmente que as relações de objeto-à- objeto correspondem às relações estrangeiro-chave- estilo em bases de dados.</span><span class="sxs-lookup"><span data-stu-id="7f850-112">It is only a happy coincidence that object-to-object relationships correspond to foreign-key-styled relationships in databases.</span></span> <span data-ttu-id="7f850-113">Acesso da propriedade em fornece uma maneira conveniente de escrever join.</span><span class="sxs-lookup"><span data-stu-id="7f850-113">Property access then provides a convenient way to write joins.</span></span>  
  
 <span data-ttu-id="7f850-114">Em relação a isso, as propriedades da relação são mais importantes no lado dos resultados de uma consulta de como parte da consulta própria.</span><span class="sxs-lookup"><span data-stu-id="7f850-114">With regard to this, relationship properties are more important on the results side of a query than as part of the query itself.</span></span> <span data-ttu-id="7f850-115">Depois que a consulta recuperou dados sobre um determinado cliente, a definição de classe indica que os clientes têm pedidos.</span><span class="sxs-lookup"><span data-stu-id="7f850-115">After the query has retrieved data about a particular customer, the class definition indicates that customers have orders.</span></span> <span data-ttu-id="7f850-116">Ou você espera é a propriedade de `Orders` de um cliente específico ser uma coleção que é preenchida com todos os pedidos do cliente.</span><span class="sxs-lookup"><span data-stu-id="7f850-116">In other words, you expect the `Orders` property of a particular customer to be a collection that is populated with all the orders from that customer.</span></span> <span data-ttu-id="7f850-117">Isso é fato do contrato que você declarou definindo classes dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="7f850-117">That is in fact the contract you declared by defining the classes in this manner.</span></span> <span data-ttu-id="7f850-118">Você espera consulte existem os pedidos mesmo se a consulta não solicitou pedidos.</span><span class="sxs-lookup"><span data-stu-id="7f850-118">You expect to see the orders there even if the query did not request orders.</span></span> <span data-ttu-id="7f850-119">Você espera seu modelo de objeto manter uma ilusão que é uma extensão de memória de base de dados com objetos relacionados imediatamente disponíveis.</span><span class="sxs-lookup"><span data-stu-id="7f850-119">You expect your object model to maintain an illusion that it is an in-memory extension of the database with related objects immediately available.</span></span>  
  
 <span data-ttu-id="7f850-120">Agora que você tem relações, você pode escrever consultas com referência às propriedades de relação definidas em suas classes.</span><span class="sxs-lookup"><span data-stu-id="7f850-120">Now that you have relationships, you can write queries by referring to the relationship properties defined in your classes.</span></span> <span data-ttu-id="7f850-121">Essas referências de relação correspondem às relações de chave estrangeira na base de dados.</span><span class="sxs-lookup"><span data-stu-id="7f850-121">These relationship references correspond to foreign-key relationships in the database.</span></span> <span data-ttu-id="7f850-122">As operações que usam essas relações traduzem a mais complexo ingressar no equivalente SQL.</span><span class="sxs-lookup"><span data-stu-id="7f850-122">Operations that use these relationships translate to more complex joins in the equivalent SQL.</span></span> <span data-ttu-id="7f850-123">Como você tiver definido uma relação (usando o atributo de <xref:System.Data.Linq.Mapping.AssociationAttribute> ), você não precisará codificar um join explícito em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7f850-123">As long as you have defined a relationship (using the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute), you do not have to code an explicit join in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 <span data-ttu-id="7f850-124">Para ajudar a manter a ilusão [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementa uma técnica chamada *carregamento diferido*.</span><span class="sxs-lookup"><span data-stu-id="7f850-124">To help maintain this illusion, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implements a technique called *deferred loading*.</span></span> <span data-ttu-id="7f850-125">Para obter mais informações, consulte [adiado contra Carregando imediata](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="7f850-125">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
 <span data-ttu-id="7f850-126">Considere a seguinte consulta SQL para projetar uma lista de `CustomerID` - `OrderID` pares:</span><span class="sxs-lookup"><span data-stu-id="7f850-126">Consider the following SQL query to project a list of `CustomerID`-`OrderID` pairs:</span></span>  
  
```  
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 <span data-ttu-id="7f850-127">Para obter os mesmos resultados usando [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], você usa a referência de propriedade de `Orders` já que existe na classe de `Customer` .</span><span class="sxs-lookup"><span data-stu-id="7f850-127">To obtain the same results by using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you use the `Orders` property reference already existing in the `Customer` class.</span></span> <span data-ttu-id="7f850-128">O `Orders` referência fornece as informações necessárias para executar a consulta e o projeto a `CustomerID` - `OrderID` pares, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="7f850-128">The `Orders` reference provides the necessary information to execute the query and project the `CustomerID`-`OrderID` pairs, as in the following code:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 <span data-ttu-id="7f850-129">Você também pode fazer o inverso.</span><span class="sxs-lookup"><span data-stu-id="7f850-129">You can also do the reverse.</span></span> <span data-ttu-id="7f850-130">Isto é, você pode ver `Orders` e usar sua referência de relação de `Customer` para acessar informações sobre o objeto associado de `Customer` .</span><span class="sxs-lookup"><span data-stu-id="7f850-130">That is, you can query `Orders` and use its `Customer` relationship reference to access information about the associated `Customer` object.</span></span> <span data-ttu-id="7f850-131">O código a seguir projeta o mesmo `CustomerID` - `OrderID` pares como antes, mas desta vez consultando `Orders` em vez de `Customers`.</span><span class="sxs-lookup"><span data-stu-id="7f850-131">The following code projects the same `CustomerID`-`OrderID` pairs as before, but this time by querying `Orders` instead of `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="7f850-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f850-132">See Also</span></span>  
 [<span data-ttu-id="7f850-133">Conceitos de consulta</span><span class="sxs-lookup"><span data-stu-id="7f850-133">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)