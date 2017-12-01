---
title: "Expressões lambda em PLINQ e TPL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 79ab0f4427e0f37259f88cd3ec0762d1582481f1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a><span data-ttu-id="70a4f-102">Expressões lambda em PLINQ e TPL</span><span class="sxs-lookup"><span data-stu-id="70a4f-102">Lambda Expressions in PLINQ and TPL</span></span>
<span data-ttu-id="70a4f-103">O biblioteca paralela de tarefas (TPL) contém vários métodos que usam uma da <xref:System.Func%601?displayProperty=nameWithType> ou <xref:System.Action?displayProperty=nameWithType> família de delegados como parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="70a4f-103">The Task Parallel Library (TPL) contains many methods that take one of the <xref:System.Func%601?displayProperty=nameWithType> or <xref:System.Action?displayProperty=nameWithType> family of delegates as input parameters.</span></span> <span data-ttu-id="70a4f-104">Você pode usar esses delegados para transmitir sua lógica de programa personalizado para o loop paralelo, a tarefa ou a consulta.</span><span class="sxs-lookup"><span data-stu-id="70a4f-104">You use these delegates to pass in your custom program logic to the parallel loop, task or query.</span></span> <span data-ttu-id="70a4f-105">Os exemplos de código para TPL, bem como o PLINQ usam expressões lambda para criar instâncias desses representantes como blocos de código embutido.</span><span class="sxs-lookup"><span data-stu-id="70a4f-105">The code examples for TPL as well as PLINQ use lambda expressions to create instances of those delegates as inline code blocks.</span></span> <span data-ttu-id="70a4f-106">Este tópico fornece uma breve introdução ao Func e Action e mostra como usar expressões lambda no PLINQ e biblioteca paralela de tarefas.</span><span class="sxs-lookup"><span data-stu-id="70a4f-106">This topic provides a brief introduction to Func and Action and shows you how to use lambda expressions in the Task Parallel Library and PLINQ.</span></span>  
  
 <span data-ttu-id="70a4f-107">**Observação** para obter mais informações sobre delegados em geral, consulte [delegados](../../csharp/programming-guide/delegates/index.md) e [delegados](../../visual-basic/programming-guide/language-features/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="70a4f-107">**Note** For more information about delegates in general, see [Delegates](../../csharp/programming-guide/delegates/index.md) and [Delegates](../../visual-basic/programming-guide/language-features/delegates/index.md).</span></span> <span data-ttu-id="70a4f-108">Para obter mais informações sobre expressões lambda em c# e [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], consulte [expressões Lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) e [expressões Lambda](~/docs/visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="70a4f-108">For more information about lambda expressions in C# and [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], see [Lambda Expressions](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) and [Lambda Expressions](~/docs/visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
## <a name="func-delegate"></a><span data-ttu-id="70a4f-109">Delegado de função</span><span class="sxs-lookup"><span data-stu-id="70a4f-109">Func Delegate</span></span>  
 <span data-ttu-id="70a4f-110">Um `Func` delegado encapsula um método que retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="70a4f-110">A `Func` delegate encapsulates a method that returns a value.</span></span> <span data-ttu-id="70a4f-111">Em uma assinatura de função, o parâmetro de tipo do último ou mais à direita sempre Especifica o tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="70a4f-111">In a Func signature, the last or rightmost type parameter always specifies the return type.</span></span> <span data-ttu-id="70a4f-112">Uma causa comum de erros do compilador é tentar passar dois parâmetros de entrada para um <xref:System.Func%602?displayProperty=nameWithType>; na verdade, esse tipo usa somente um parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="70a4f-112">One common cause of compiler errors is to attempt to pass in two input parameters to a <xref:System.Func%602?displayProperty=nameWithType>; in fact this type takes only one input parameter.</span></span> <span data-ttu-id="70a4f-113">A biblioteca de classes do Framework define 17 versões do `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, e assim por diante até por meio de <xref:System.Func%6017?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="70a4f-113">The Framework Class Library defines 17 versions of `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, and so on up through <xref:System.Func%6017?displayProperty=nameWithType>.</span></span>  
  
## <a name="action-delegate"></a><span data-ttu-id="70a4f-114">Delegado de ação</span><span class="sxs-lookup"><span data-stu-id="70a4f-114">Action Delegate</span></span>  
 <span data-ttu-id="70a4f-115">Um <xref:System.Action?displayProperty=nameWithType> delegado encapsula um método (Sub no [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) que não retorna um valor ou retorna [void](~/docs/csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="70a4f-115">A <xref:System.Action?displayProperty=nameWithType> delegate encapsulates a method (Sub in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) that does not return a value, or returns [void](~/docs/csharp/language-reference/keywords/void.md).</span></span> <span data-ttu-id="70a4f-116">Uma assinatura de tipo de ação, os parâmetros de tipo representam apenas os parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="70a4f-116">In an Action type signature, the type parameters represent only input parameters.</span></span> <span data-ttu-id="70a4f-117">Como Func, a biblioteca de classes do Framework define 17 versões de ação, de uma versão que não tem nenhum parâmetro de tipo por meio de uma versão que tenha 16 parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="70a4f-117">Like Func, the Framework Class Library defines 17 versions of Action, from a version that has no type parameters up through a version that has 16 type parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70a4f-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="70a4f-118">Example</span></span>  
 <span data-ttu-id="70a4f-119">O exemplo a seguir para o <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> método mostra como express delegados Func e Action usando expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="70a4f-119">The following example for the <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> method shows how to express both Func and Action delegates by using lambda expressions.</span></span>  
  
 [!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
 [!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]  
  
## <a name="see-also"></a><span data-ttu-id="70a4f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70a4f-120">See Also</span></span>  
 [<span data-ttu-id="70a4f-121">Programação paralela</span><span class="sxs-lookup"><span data-stu-id="70a4f-121">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)