---
title: "Níveis de confiança de segurança de acesso a recursos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb5be924-317d-4d69-b33a-3d18ecfb9d6e
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d4cefe74b745eb4a1c71124176985c548f9b1244
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="security-trust-levels-in-accessing-resources"></a><span data-ttu-id="20da6-102">Níveis de confiança de segurança de acesso a recursos</span><span class="sxs-lookup"><span data-stu-id="20da6-102">Security Trust Levels in Accessing Resources</span></span>
<span data-ttu-id="20da6-103">Este tópico discute como o acesso está restrito a tipos de recursos que <xref:System.Transactions> expõe.</span><span class="sxs-lookup"><span data-stu-id="20da6-103">This topic discusses how access is restricted on the types of resources that <xref:System.Transactions> exposes.</span></span>  
  
 <span data-ttu-id="20da6-104">Há três principais níveis de confiança para <xref:System.Transactions>.</span><span class="sxs-lookup"><span data-stu-id="20da6-104">There are three main levels of trust for <xref:System.Transactions>.</span></span> <span data-ttu-id="20da6-105">Os níveis de confiança são definidos com base nos tipos de recursos que <xref:System.Transactions> expõe e o nível de confiança deve ser necessária para acessar esses recursos.</span><span class="sxs-lookup"><span data-stu-id="20da6-105">The trust levels are defined based on the types of resources that <xref:System.Transactions> exposes, and the level of trust that should be required to access those resources.</span></span> <span data-ttu-id="20da6-106">Os recursos que <xref:System.Transactions> fornece acesso a são recursos ampla do sistema, recursos ampla do processo compartilhado e memória do sistema.</span><span class="sxs-lookup"><span data-stu-id="20da6-106">The resources that <xref:System.Transactions> provides access to are system memory, shared process wide resources, and system wide resources.</span></span> <span data-ttu-id="20da6-107">Os níveis são:</span><span class="sxs-lookup"><span data-stu-id="20da6-107">The levels are:</span></span>  
  
-   <span data-ttu-id="20da6-108">**AllowPartiallyTrustedCallers** (APTCA) para aplicativos que usam transações dentro de um único domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="20da6-108">**AllowPartiallyTrustedCallers** (APTCA) for applications using transactions within a single application domain.</span></span>  
  
-   <span data-ttu-id="20da6-109">**DistributedTransactionPermission** (DTP) para aplicativos que usam transações distribuídas.</span><span class="sxs-lookup"><span data-stu-id="20da6-109">**DistributedTransactionPermission** (DTP) for applications using distributed transactions.</span></span>  
  
-   <span data-ttu-id="20da6-110">Confiança total para recursos duráveis, aplicativos de gerenciamento de configuração e os aplicativos herdados de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="20da6-110">Full trust for durable resources, configuration management applications, and legacy interop applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20da6-111">Você não deve chamar qualquer uma das interfaces de inscrição com contextos representados.</span><span class="sxs-lookup"><span data-stu-id="20da6-111">You should not call any of the enlistment interfaces with impersonated contexts.</span></span>  
  
## <a name="trust-levels"></a><span data-ttu-id="20da6-112">Níveis de confiança</span><span class="sxs-lookup"><span data-stu-id="20da6-112">Trust Levels</span></span>  
  
### <a name="aptca-partial-trust"></a><span data-ttu-id="20da6-113">APTCA (confiança parcial)</span><span class="sxs-lookup"><span data-stu-id="20da6-113">APTCA (Partial Trust)</span></span>  
 <span data-ttu-id="20da6-114">O <xref:System.Transactions> assembly pode ser chamado por código parcialmente confiável, porque ela foi marcada com o **AllowPartiallyTrustedCallers** atributo (APTCA).</span><span class="sxs-lookup"><span data-stu-id="20da6-114">The <xref:System.Transactions> assembly can be called by partially trusted code because it has been marked with the **AllowPartiallyTrustedCallers** attribute (APTCA).</span></span> <span data-ttu-id="20da6-115">Esse atributo essencialmente remove o implícita <xref:System.Security.Permissions.SecurityAction.LinkDemand> para o **FullTrust** permissão conjunto caso contrário colocado automaticamente em cada método publicamente acessível em cada tipo.</span><span class="sxs-lookup"><span data-stu-id="20da6-115">This attribute essentially removes the implicit <xref:System.Security.Permissions.SecurityAction.LinkDemand> for the **FullTrust** permission set that is otherwise automatically placed on each publicly accessible method in each type.</span></span> <span data-ttu-id="20da6-116">No entanto, alguns tipos e membros ainda requerem permissões mais fortes.</span><span class="sxs-lookup"><span data-stu-id="20da6-116">However, some types and members still require stronger permissions.</span></span>  
  
 <span data-ttu-id="20da6-117">O atributo APTCA permite que aplicativos usem as transações em confiança parcial em um único domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="20da6-117">The APTCA attribute enables applications to use transactions in partial trust within a single application domain.</span></span> <span data-ttu-id="20da6-118">Isso permite que as transações não escalonados e inscrições voláteis que podem ser usadas para tratamento de erros.</span><span class="sxs-lookup"><span data-stu-id="20da6-118">This enables non-escalated transactions and volatile enlistments that can be used for error handling.</span></span> <span data-ttu-id="20da6-119">Um exemplo disso é uma tabela de hash transacionado e um aplicativo que utiliza.</span><span class="sxs-lookup"><span data-stu-id="20da6-119">One example of this is a transacted hash table and an application that uses it.</span></span> <span data-ttu-id="20da6-120">Dados podem ser adicionados ao e removidos da tabela de hash em uma única transação.</span><span class="sxs-lookup"><span data-stu-id="20da6-120">Data can be added to and removed from the hash table under a single transaction.</span></span> <span data-ttu-id="20da6-121">Se a transação é posteriormente revertida, todas as alterações feitas na tabela de hash em transação podem ser desfeitas.</span><span class="sxs-lookup"><span data-stu-id="20da6-121">If the transaction is later rolled back, all of the changes made to the hash table under that transaction can be undone.</span></span>  
  
### <a name="distributedtransactionpermission-dtp"></a><span data-ttu-id="20da6-122">DistributedTransactionPermission (DTP)</span><span class="sxs-lookup"><span data-stu-id="20da6-122">DistributedTransactionPermission (DTP)</span></span>  
 <span data-ttu-id="20da6-123">Quando um <xref:System.Transactions> transação será escalada para ser gerenciado pelo MSDTC, <xref:System.Transactions> demandas de <xref:System.Transactions.DistributedTransactionPermission> (DTP) para criar a transação distribuída.</span><span class="sxs-lookup"><span data-stu-id="20da6-123">When a <xref:System.Transactions> transaction is escalated to be managed by MSDTC, <xref:System.Transactions> demands the <xref:System.Transactions.DistributedTransactionPermission> (DTP) to create the distributed transaction.</span></span> <span data-ttu-id="20da6-124">Isso significa que o código que faz com que a transação ser escalados (como por meio de serialização ou mais inscrições duráveis) precisa ser concedida DTP.</span><span class="sxs-lookup"><span data-stu-id="20da6-124">This means that the code that causes the transaction to be escalated (such as through serialization or additional durable enlistments) would need to be granted DTP.</span></span> <span data-ttu-id="20da6-125">O código que criou o <xref:System.Transactions> transação não necessariamente precisa ter essa permissão.</span><span class="sxs-lookup"><span data-stu-id="20da6-125">The code that originally created the <xref:System.Transactions> transaction does not necessarily need to possess this permission.</span></span>  
  
### <a name="fulltrust-link-demands"></a><span data-ttu-id="20da6-126">Demandas de Link FullTrust</span><span class="sxs-lookup"><span data-stu-id="20da6-126">FullTrust Link Demands</span></span>  
 <span data-ttu-id="20da6-127">Esse nível de permissão destina-se para restringir os aplicativos que gravam dados Recursos duráveis.</span><span class="sxs-lookup"><span data-stu-id="20da6-127">This permission level is intended to restrict applications that are writing to durable resources.</span></span> <span data-ttu-id="20da6-128">Em caso de falha, o aplicativo precisa ser capaz de recuperar-se com o Gerenciador de transações para determinar o resultado final da transação, para que ele possa atualizar dados permanente.</span><span class="sxs-lookup"><span data-stu-id="20da6-128">Upon failure, the application needs to be able to recover with the transaction manager to determine the final outcome of the transaction, so that it can update permanent data.</span></span> <span data-ttu-id="20da6-129">Esse tipo de aplicativo é conhecido como um Gerenciador de fonte durável.</span><span class="sxs-lookup"><span data-stu-id="20da6-129">This type of application is known as a durable source manager.</span></span> <span data-ttu-id="20da6-130">Um exemplo clássico desse tipo de aplicativo é SQL.</span><span class="sxs-lookup"><span data-stu-id="20da6-130">A classic example of this type of application is SQL.</span></span>  
  
 <span data-ttu-id="20da6-131">Para habilitar a recuperação, esse tipo de aplicativo tem a capacidade de consumir permanentemente os recursos do sistema.</span><span class="sxs-lookup"><span data-stu-id="20da6-131">To enable recovery, this type of application has the ability to permanently consume system resources.</span></span> <span data-ttu-id="20da6-132">Isso ocorre porque o Gerenciador de transações recuperável deve se lembrar de transações que foram confirmadas até que ele possa confirmar que todos os gerenciadores de recursos duráveis que participam da transação tem recebido o resultado.</span><span class="sxs-lookup"><span data-stu-id="20da6-132">This is because the recoverable transaction manager must remember transactions that have committed until it can confirm that all durable resource managers that are participating in the transaction have received the outcome.</span></span> <span data-ttu-id="20da6-133">Portanto, esse tipo de aplicativo requer confiança total e não deve ser executado, a menos que nível de confiança recebeu.</span><span class="sxs-lookup"><span data-stu-id="20da6-133">Therefore, this type of application requires full trust and should not be run unless that level of trust has been granted.</span></span>  
  
 <span data-ttu-id="20da6-134">Para obter mais informações sobre inscrições duráveis e recuperação, consulte o [inscrição recursos como participantes em uma transação](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) e [executar recuperação](../../../../docs/framework/data/transactions/performing-recovery.md) tópicos.</span><span class="sxs-lookup"><span data-stu-id="20da6-134">For more information on durable enlistments and recovery, see the [Enlisting Resources as Participants in a Transaction](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) and [Performing Recovery](../../../../docs/framework/data/transactions/performing-recovery.md) topics.</span></span>  
  
 <span data-ttu-id="20da6-135">Aplicativos que executam o trabalho com herdado interoperabilidade com COM+ também precisam ter confiança total.</span><span class="sxs-lookup"><span data-stu-id="20da6-135">Applications that perform legacy interop work with COM+ are also required to have full trust.</span></span>  
  
 <span data-ttu-id="20da6-136">A seguir está uma lista de tipos e membros que não podem ser chamados por parcialmente confiável código porque elas são decoradas com o **FullTrust** atributo de segurança declarativa:</span><span class="sxs-lookup"><span data-stu-id="20da6-136">The following is a list of types and members that are not callable by partially trusted code because they are decorated with the **FullTrust** declarative security attribute:</span></span>  
  
 `PermissionSetAttribute(SecurityAction.LinkDemand, Name := "FullTrust")`  
  
-   <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>  
  
-   <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>  
  
-   <xref:System.Transactions.TransactionInterop>  
  
-   <xref:System.Transactions.TransactionManager.DistributedTransactionStarted>  
  
-   <xref:System.Transactions.HostCurrentTransactionCallback>  
  
-   <xref:System.Transactions.TransactionManager.Reenlist%2A>  
  
-   <xref:System.Transactions.TransactionManager.RecoveryComplete%2A>  
  
-   <xref:System.Transactions.TransactionScope.%23ctor%28System.Transactions.TransactionScopeOption%2CSystem.Transactions.TransactionOptions%2CSystem.Transactions.EnterpriseServicesInteropOption%29>  
  
 <span data-ttu-id="20da6-137">Somente o chamador imediato é necessário ter o **FullTrust** conjunto de permissões para usar tipos ou métodos acima.</span><span class="sxs-lookup"><span data-stu-id="20da6-137">Only the immediate caller is required to possess the **FullTrust** permission set to use the above types or methods.</span></span>