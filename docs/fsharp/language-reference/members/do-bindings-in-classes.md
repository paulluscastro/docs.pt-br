---
title: "Associações do em classes (F#)"
description: "Saiba como usar uma linguagem F # 'do' associação em uma definição de classe, que executa ações quando o objeto é criado ou quando o tipo é usado pela primeira vez."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 78987cb8-bdba-46e2-b5b2-994c83fe42c4
ms.openlocfilehash: f9582338306d87c3dd799425083037cc95b31b1e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="do-bindings-in-classes"></a><span data-ttu-id="931ef-104">Associações do em classes</span><span class="sxs-lookup"><span data-stu-id="931ef-104">do Bindings in Classes</span></span>

<span data-ttu-id="931ef-105">Um `do` associação em uma definição de classe executa ações quando o objeto for construído ou, para um static `do` associação, quando o tipo de primeira será usado.</span><span class="sxs-lookup"><span data-stu-id="931ef-105">A `do` binding in a class definition performs actions when the object is constructed or, for a static `do` binding, when the type is first used.</span></span>


## <a name="syntax"></a><span data-ttu-id="931ef-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="931ef-106">Syntax</span></span>

```fsharp
[static] do expression
```

## <a name="remarks"></a><span data-ttu-id="931ef-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="931ef-107">Remarks</span></span>
<span data-ttu-id="931ef-108">Um `do` associação aparece junto com ou após `let` associações, mas antes de definições de membro em uma definição de classe.</span><span class="sxs-lookup"><span data-stu-id="931ef-108">A `do` binding appears together with or after `let` bindings but before member definitions in a class definition.</span></span> <span data-ttu-id="931ef-109">Embora o `do` palavra-chave é opcional para `do` associações no nível de módulo, não é opcional para `do` associações em uma definição de classe.</span><span class="sxs-lookup"><span data-stu-id="931ef-109">Although the `do` keyword is optional for `do` bindings at the module level, it is not optional for `do` bindings in a class definition.</span></span>

<span data-ttu-id="931ef-110">Para a construção de todos os objetos de qualquer tipo, não estático fornecido `do` associações e não-estático `let` associações são executadas na ordem em que aparecem na definição de classe.</span><span class="sxs-lookup"><span data-stu-id="931ef-110">For the construction of every object of any given type, non-static `do` bindings and non-static `let` bindings are executed in the order in which they appear in the class definition.</span></span> <span data-ttu-id="931ef-111">Vários `do` associações podem ocorrer em um tipo.</span><span class="sxs-lookup"><span data-stu-id="931ef-111">Multiple `do` bindings can occur in one type.</span></span> <span data-ttu-id="931ef-112">O não-estático `let` associações e não-estático `do` associações tornam-se o corpo do construtor primário.</span><span class="sxs-lookup"><span data-stu-id="931ef-112">The non-static `let` bindings and the non-static `do` bindings become the body of the primary constructor.</span></span> <span data-ttu-id="931ef-113">O código de não-estático `do` seção associações pode referenciar os parâmetros do construtor primário e todos os valores ou funções que estão definidas no `let` seção associações.</span><span class="sxs-lookup"><span data-stu-id="931ef-113">The code in the non-static `do` bindings section can reference the primary constructor parameters and any values or functions that are defined in the `let` bindings section.</span></span>

<span data-ttu-id="931ef-114">Não-estático `do` associações podem acessar membros da classe, contanto que a classe tenha um identificador de autoatendimento que é definido por um `as` palavra-chave na classe de título e, desde que todos os usos dos membros são qualificados com o identificador de autoatendimento para a classe.</span><span class="sxs-lookup"><span data-stu-id="931ef-114">Non-static `do` bindings can access members of the class as long as the class has a self identifier that is defined by an `as` keyword in the class heading, and as long as all uses of those members are qualified with the self identifier for the class.</span></span>

<span data-ttu-id="931ef-115">Porque `let` associações inicializar os campos particulares de uma classe, que é geralmente necessário para garantir que os membros se comportam como esperado, `do` associações são geralmente colocadas após `let` associações de forma que o código no `do` pode associação Execute com um objeto completamente inicializado.</span><span class="sxs-lookup"><span data-stu-id="931ef-115">Because `let` bindings initialize the private fields of a class, which is often necessary to guarantee that members behave as expected, `do` bindings are usually put after `let` bindings so that code in the `do` binding can execute with a fully initialized object.</span></span> <span data-ttu-id="931ef-116">Se seu código tentar usar um membro antes da inicialização é concluída, um InvalidOperationException é gerado.</span><span class="sxs-lookup"><span data-stu-id="931ef-116">If your code attempts to use a member before the initialization is complete, an InvalidOperationException is raised.</span></span>

<span data-ttu-id="931ef-117">Estático `do` associações podem fazer referência a membros estáticos ou campos de circunscrição de classe, mas não membros ou campos de instância.</span><span class="sxs-lookup"><span data-stu-id="931ef-117">Static `do` bindings can reference static members or fields of the enclosing class but not instance members or fields.</span></span> <span data-ttu-id="931ef-118">Estático `do` associações se tornam parte do inicializador estático da classe, que é garantido para executar antes que a classe é usada pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="931ef-118">Static `do` bindings become part of the static initializer for the class, which is guaranteed to execute before the class is first used.</span></span>

<span data-ttu-id="931ef-119">Atributos são ignorados para `do` associações em tipos.</span><span class="sxs-lookup"><span data-stu-id="931ef-119">Attributes are ignored for `do` bindings in types.</span></span> <span data-ttu-id="931ef-120">Se um atributo é necessário para o código que é executado em um `do` de associação, ela deverá ser aplicada ao construtor primário.</span><span class="sxs-lookup"><span data-stu-id="931ef-120">If an attribute is required for code that executes in a `do` binding, it must be applied to the primary constructor.</span></span>

<span data-ttu-id="931ef-121">No código a seguir, uma classe tem um estático `do` de associação e não-estático `do` associação.</span><span class="sxs-lookup"><span data-stu-id="931ef-121">In the following code, a class has a static `do` binding and a non-static `do` binding.</span></span> <span data-ttu-id="931ef-122">O objeto tem um construtor que tem dois parâmetros, `a` e `b`, e os dois campos particulares são definidos no `let` associações para a classe.</span><span class="sxs-lookup"><span data-stu-id="931ef-122">The object has a constructor that has two parameters, `a` and `b`, and two private fields are defined in the `let` bindings for the class.</span></span> <span data-ttu-id="931ef-123">Duas propriedades também são definidas.</span><span class="sxs-lookup"><span data-stu-id="931ef-123">Two properties are also defined.</span></span> <span data-ttu-id="931ef-124">Todos eles estão no escopo em não-estático `do` seção associações, conforme ilustrado pela linha que imprime todos esses valores.</span><span class="sxs-lookup"><span data-stu-id="931ef-124">All of these are in scope in the non-static `do` bindings section, as is illustrated by the line that prints all those values.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

<span data-ttu-id="931ef-125">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="931ef-125">The output is as follows.</span></span>

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a><span data-ttu-id="931ef-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="931ef-126">See Also</span></span>
[<span data-ttu-id="931ef-127">Membros</span><span class="sxs-lookup"><span data-stu-id="931ef-127">Members</span></span>](index.md)

[<span data-ttu-id="931ef-128">Classes</span><span class="sxs-lookup"><span data-stu-id="931ef-128">Classes</span></span>](../classes.md)

[<span data-ttu-id="931ef-129">Construtores</span><span class="sxs-lookup"><span data-stu-id="931ef-129">Constructors</span></span>](constructors.md)

[<span data-ttu-id="931ef-130">`let`Associações em Classes</span><span class="sxs-lookup"><span data-stu-id="931ef-130">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)

[<span data-ttu-id="931ef-131">`do`Associações</span><span class="sxs-lookup"><span data-stu-id="931ef-131">`do` Bindings</span></span>](../functions/do-Bindings.md)