---
title: Tipo de dados curto (Visual Basic)
ms.date: 01/31/2018
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
author: rpetrusha
ms.author: ronpet
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: 10c9869d4fb84cd013b22bc791bd31fad745f3d3
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="short-data-type-visual-basic"></a>Tipo de dados curto (Visual Basic)
Armazena inteiros de 16 bits (2 bytes) que variam de -32.768 a 32.767.  
  
## <a name="remarks"></a>Comentários  
 Use o `Short` tipo de dados para conter valores inteiros que não requerem a largura total de dados de `Integer`. Em alguns casos, o common language runtime pode empacotar sua `Short` variáveis próximas uma da outra e economizar memória.  
  
 O valor padrão de `Short` é 0.  
  
## <a name="literal-assignments"></a>Atribuições de literal

Você pode declarar e inicializar uma `Short` variável atribuindo a ele um literal decimal, hexadecimal literal, um literal octal, ou (começando com Visual Basic 2017) um literal binário. Se o literal inteiro estiver fora do intervalo de `Short` (ou seja, se for menor que <xref:System.Int16.MinValue?displayProperty=nameWithType> ou maior que <xref:System.Int16.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.

No exemplo a seguir, inteiros igual à 1,034 que são representados como decimal, hexadecimal, e literais binárias são implicitamente convertidos do [inteiro](integer-data-type.md) para `Short` valores.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> Use o prefixo `&h` ou `&H` para denotar um hexadecimal literal, o prefixo `&b` ou `&B` para denotar um literal binário e o prefixo `&o` ou `&O` para denotar um literal octal. Literais decimais não têm nenhum prefixo.

A partir do Visual Basic de 2017, você também pode usar o caractere de sublinhado, `_`, como um separador de dígito para melhorar a legibilidade, como o exemplo a seguir mostra.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

A partir do Visual Basic 15,5, você também pode usar o caractere de sublinhado (`_`) como um separador à esquerda entre o prefixo e os dígitos hexadecimais, binários ou octais. Por exemplo:

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Literais numéricos também podem incluir o `S` [caractere de tipo](../../programming-guide\language-features\data-types/type-characters.md) para denotar o `Short` tipo de dados, como mostra o exemplo a seguir.

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a>Dicas de programação

-   **Ampliação.** O `Short` tipo de dados amplia a `Integer`, `Long`, `Decimal`, `Single`, ou `Double`. Isso significa que você pode converter `Short` em qualquer um desses tipos sem a ocorrência de um erro <xref:System.OverflowException?displayProperty=nameWithType>.  
  
-   **Caracteres de tipo.** Acrescentar o caractere de tipo literal `S` a um literal o força ao tipo de dados `Short`. `Short`não tem nenhum caractere de tipo identificador.  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.Int16?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Consulte também

 <xref:System.Int16?displayProperty=nameWithType>  
 [Tipos de Dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Tipo de Dados Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [Tipo de Dados Long](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
