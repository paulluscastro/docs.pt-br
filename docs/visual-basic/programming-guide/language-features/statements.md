---
title: Instruções no Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], declaring
- colons (:) [Visual Basic]
- constants [Visual Basic], defining
- underlines
- constants [Visual Basic], statements
- blue underline [Visual Basic]
- procedures [Visual Basic], statements
- variables [Visual Basic], assigning
- line breaks [Visual Basic], in code
- executable statements [Visual Basic]
- variables [Visual Basic], defining
- statements [Visual Basic], about statements
ms.assetid: fcfdee1a-82b7-4846-98f7-9ca3f5160089
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: beb33b8f2c30723158e41244cbb5c9cfca108a53
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="statements-in-visual-basic"></a>Instruções no Visual Basic
Uma instrução no Visual Basic é uma instrução completa. Ele pode conter as palavras-chave, operadores, variáveis, constantes e expressões. Cada instrução pertence a uma das seguintes categorias:  
  
-   **Instruções de declaração**, que o nome de uma variável, uma constante ou um procedimento e também pode especificar um tipo de dados.  
  
-   **Instruções executáveis**, qual iniciar ações. Essas instruções podem chamar um método ou função e um loop ou branch por meio de blocos de código. Instruções executáveis incluem **instruções de atribuição**, que atribui um valor ou expressão a uma variável ou constante.  
  
 Este tópico descreve cada categoria. Além disso, este tópico descreve como combinar várias instruções em uma única linha e uma instrução continue em várias linhas.  
  
## <a name="declaration-statements"></a>Instruções de declaração  
 Você pode usar instruções de declaração para nomear e definir procedimentos, variáveis, propriedades, matrizes e constantes. Quando você declara um elemento de programação, você também pode definir o tipo de dados, o nível de acesso e o escopo. Para obter mais informações, consulte [características do elemento declarado](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).  
  
 O exemplo a seguir contém três declarações.  
  
 [!code-vb[VbVbalrStatements#80](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_1.vb)]  
  
 A primeira declaração é o `Sub` instrução. Junto com sua correspondência `End Sub` instrução, ele declara um procedimento denominado `applyFormat`. Ela também especifica que `applyFormat` é `Public`, que significa que qualquer código que pode fazer referência a ele pode chamá-lo.  
  
 A segunda declaração é o `Const` instrução que declara a constante `limit`, especificando o `Integer` tipo de dados e um valor de 33.  
  
 A terceira declaração é a `Dim` instrução que declara a variável `thisWidget`. O tipo de dados é um objeto específico, ou seja, um objeto criado a partir de `Widget` classe. Você pode declarar uma variável de qualquer tipo de dados elementar ou de qualquer tipo de objeto que é exposto no aplicativo que você está usando.  
  
### <a name="initial-values"></a>Valores iniciais  
 Quando o código que contém uma instrução de declaração é executado, o Visual Basic reserva de memória exigida para o elemento declarado. Se o elemento contém um valor, o Visual Basic o inicializa com o valor padrão para seu tipo de dados. Para obter mais informações, consulte "Comportamento" em [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
 Você pode atribuir um valor inicial para uma variável como parte de sua declaração, como mostra o exemplo a seguir.  
  
 [!code-vb[VbVbalrStatements#81](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_2.vb)]  
  
 Se uma variável é uma variável de objeto, você pode criar explicitamente uma instância de sua classe quando você declará-la usando o [novo operador](../../../visual-basic/language-reference/operators/new-operator.md) palavra-chave, como o exemplo a seguir ilustra.  
  
 [!code-vb[VbVbalrStatements#82](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_3.vb)]  
  
 Observe que o valor inicial especificado em uma instrução de declaração não é atribuído a uma variável até que a execução atinge sua instrução de declaração. Até lá, a variável contém o valor padrão para seu tipo de dados.  
  
## <a name="executable-statements"></a>Instruções executáveis  
 Uma instrução executável executa uma ação. Ele pode chamar um procedimento, a ramificação para outro lugar no código, o loop por meio de várias instruções, ou avaliar uma expressão. Uma instrução de atribuição é um caso especial de uma instrução executável.  
  
 O exemplo a seguir usa um `If...Then...Else` estrutura para executar diferentes blocos de código com base no valor de uma variável de controle. Em cada bloco de código, um `For...Next` loop é executado em um número especificado de vezes.  
  
 [!code-vb[VbVbalrStatements#83](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_4.vb)]  
  
 O `If` instrução no exemplo anterior verifica o valor do parâmetro `clockwise`. Se o valor for `True`, ele chama o `spinClockwise` método `aWidget`. Se o valor for `False`, ele chama o `spinCounterClockwise` método `aWidget`. O `If...Then...Else` termina de estrutura de controle com `End If`.  
  
 O `For...Next` loop em cada bloco chama o método apropriado um número de vezes igual ao valor da `revolutions` parâmetro.  
  
## <a name="assignment-statements"></a>Instruções de atribuição  
 Instruções de atribuição realizarem operações de atribuição, que consistem em colocar o valor à direita do operador de atribuição (`=`) e armazená-lo no elemento à esquerda, como no exemplo a seguir.  
  
 [!code-vb[VbVbalrStatements#73](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_5.vb)]  
  
 No exemplo anterior, a instrução de atribuição armazena o valor literal 42 na variável `v`.  
  
### <a name="eligible-programming-elements"></a>Elementos de programação qualificados  
 O elemento de programação no lado esquerdo do operador de atribuição deve ser capaz de aceitar e armazenar um valor. Isso significa que ele deve ser uma variável ou propriedade que não seja [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md), ou deve ser um elemento de matriz. No contexto de uma instrução de atribuição, esse elemento às vezes é chamado um *lvalue*, para "valor à esquerda".  
  
 O valor à direita do operador de atribuição é gerado por uma expressão, que pode consistir em qualquer combinação de literais, constantes, variáveis, propriedades, elementos de matriz, outras expressões ou chamadas de função. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbalrStatements#74](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_6.vb)]  
  
 O exemplo anterior adiciona o valor armazenado na variável `y` para o valor armazenado na variável `z`e, em seguida, adiciona o valor retornado pela chamada à função `findResult`. O valor total dessa expressão, em seguida, é armazenado na variável `x`.  
  
### <a name="data-types-in-assignment-statements"></a>Tipos de dados em instruções de atribuição  
 Além dos valores numéricos, o operador de atribuição também pode atribuir `String` valores, como mostra o exemplo a seguir.  
  
 [!code-vb[VbVbalrStatements#75](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_7.vb)]  
  
 Você também pode atribuir `Boolean` valores, usando um `Boolean` literal ou um `Boolean` expressão, como o exemplo a seguir ilustra.  
  
 [!code-vb[VbVbalrStatements#76](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_8.vb)]  
  
 Da mesma forma, você pode atribuir os valores apropriados para elementos de programação do `Char`, `Date`, ou `Object` tipo de dados. Você também pode atribuir uma instância do objeto para um elemento declarado como a classe da qual essa instância é criada.  
  
### <a name="compound-assignment-statements"></a>Instruções de atribuição compostas  
 *Instruções de atribuição compostas* primeiro executar uma operação em uma expressão antes de atribuí-la a um elemento de programação. O exemplo a seguir ilustra um destes operadores `+=`, que incrementa o valor da variável no lado esquerdo do operador pelo valor da expressão à direita.  
  
 [!code-vb[VbVbalrStatements#77](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_9.vb)]  
  
 O exemplo anterior adiciona 1 para o valor de `n`e, em seguida, armazena esse novo valor em `n`. É uma abreviação equivalentes a instrução a seguir:  
  
 [!code-vb[VbVbalrStatements#78](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_10.vb)]  
  
 Uma variedade de operações de atribuição composta pode ser executada usando operadores desse tipo. Para obter uma lista de mais informações sobre eles e esses operadores, consulte [operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md).  
  
 O operador de atribuição de concatenação (`&=`) é útil para adicionar uma cadeia de caracteres ao final da já existentes cadeias de caracteres, como mostra o exemplo a seguir.  
  
 [!code-vb[VbVbalrStatements#79](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_11.vb)]  
  
### <a name="type-conversions-in-assignment-statements"></a>Conversões de tipo em instruções de atribuição  
 O valor que você atribui a uma variável, propriedade ou elemento de matriz deve ser de um tipo de dados apropriado para o elemento de destino. Em geral, você deve tentar gerar um valor do mesmo tipo de dados que o elemento de destino. No entanto, alguns tipos podem ser convertidos em outros tipos durante a atribuição.  
  
 Para obter informações sobre como converter entre tipos de dados, consulte [conversões de tipo no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md). Em suma, Visual Basic automaticamente converte um valor de um determinado tipo em qualquer outro tipo ao qual será ampliada. Um *conversões ampliadoras* é um em que sempre terá êxito em tempo de execução e não perderá os dados. Por exemplo, o Visual Basic converte um `Integer` valor `Double` quando apropriado, como `Integer` amplia a `Double`. Para obter mais informações, consulte [Ampliando e restringindo conversões](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 *Conversões de estreitamento* (aquelas que não são de ampliação) realizar um risco de falha em tempo de execução ou de perda de dados. Você pode executar uma conversão de restrição explicitamente usando uma função de conversão de tipo, ou você pode instruir o compilador para executar todas as conversões implicitamente pela configuração `Option Strict Off`. Para obter mais informações, consulte [conversões explícitas e implícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).  
  
## <a name="putting-multiple-statements-on-one-line"></a>Colocar várias instruções em uma linha  
 Você pode ter várias instruções em uma única linha, separada por dois-pontos (`:`) caracteres. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbalrStatements#70](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_12.vb)]  
  
 Embora ocasionalmente conveniente, essa forma de sintaxe faz com que seu código difíceis de ler e manter. Portanto, é recomendável que você mantenha uma instrução em uma linha.  
  
## <a name="continuing-a-statement-over-multiple-lines"></a>Continuar uma instrução em várias linhas  
 Uma instrução geralmente se encaixa em uma única linha, mas quando ele for muito grande, você pode continuá-lo para a próxima linha usando uma sequência de continuação de linha, que consiste em um espaço, seguido por um caractere de sublinhado (`_`) seguido por um retorno de carro. No exemplo a seguir, o `MsgBox` instrução executável é continuada em duas linhas.  
  
 [!code-vb[VbVbalrStatements#71](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_13.vb)]  
  
### <a name="implicit-line-continuation"></a>Continuação de linha implícita  
 Em muitos casos, você pode continuar uma instrução na próxima linha consecutiva sem usar o caractere de sublinhado (_). A tabela a seguir lista os elementos de sintaxe que implicitamente continuam a instrução na próxima linha de código.  
  
|Elemento de sintaxe|Exemplo|  
|---|---|  
|Depois de uma vírgula (`,`).|[!code-vb[VbVbalrLineContinuation#1](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_14.vb)]|  
|Após um parêntese de abertura (`(`) ou antes de um parêntese de fechamento (`)`).|[!code-vb[VbVbalrLineContinuation#2](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_15.vb)]|  
|Depois de uma chave aberta (`{`) ou antes de uma chave de fechamento (`}`).|[!code-vb[VbVbalrLineContinuation#3](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_16.vb)]<br /><br /> Para obter mais informações, consulte [inicializadores de objeto: tipos nomeados e anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) ou [inicializadores de coleção](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).|  
|Depois de um open expressão inserida (`<%=`) ou antes do fechamento de uma expressão inserida (`%>`) dentro de um literal XML.|[!code-vb[VbVbalrLineContinuation#4](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_17.vb)]<br /><br /> Para obter mais informações, consulte [expressões inseridas no XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
|Após o operador de concatenação (`&`).|[!code-vb[VbVbcnConventions#9](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_18.vb)]<br /><br /> Para obter mais informações, consulte [operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Depois de operadores de atribuição (`=`, `&=`, `:=`, `+=`, `-=`, `*=`, `/=`, `\=`, `^=`, `<<=`, `>>=`).|[!code-vb[VbVbalrLineContinuation#5](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_19.vb)]<br /><br /> Para obter mais informações, consulte [operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Depois de operadores binários (`+`, `-`, `/`, `*`, `Mod`, `<>`, `<`, `>`, `<=`, `>=`, `^`, `>>`, `<<`, `And`, `AndAlso`, `Or`, `OrElse`, `Like`, `Xor`) dentro de uma expressão.|[!code-vb[VbVbalrLineContinuation#7](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_20.vb)]<br /><br /> Para obter mais informações, consulte [operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Após o `Is` e `IsNot` operadores.|[!code-vb[VbVbalrLineContinuation#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_21.vb)]<br /><br /> Para obter mais informações, consulte [operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Depois de um caractere de qualificador de membro (`.`) e antes do nome do membro. No entanto, você deve incluir um caractere de continuação de linha (_), um caractere de qualificador de membro a seguir quando você estiver usando o `With` instrução ou fornecer valores na lista de inicialização para um tipo. Considere a possibilidade de quebra de linha após o operador de atribuição (por exemplo, `=`) quando você estiver usando `With` instruções ou listas de inicialização do objeto.|[!code-vb[VbVbalrLineContinuation#5](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_19.vb)]<br />[!code-vb[VbVbalrLineContinuation#14](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_22.vb)]<br /><br /> Para obter mais informações, consulte [com... Terminar com a instrução](../../../visual-basic/language-reference/statements/with-end-with-statement.md) ou [inicializadores de objeto: tipos nomeados e anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).|  
|Depois de um qualificador de propriedade de eixo XML (`.` ou `.@` ou `...`). No entanto, você deve incluir um caractere de continuação de linha (_) quando você especificar um qualificador de membro quando você estiver usando o `With` palavra-chave.|[!code-vb[VbVbalrLineContinuation#9](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_23.vb)]<br /><br /> Para obter mais informações, consulte [propriedades de eixo XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).|  
|Depois de um menor-que (<) ou antes de um maior-sinal (`>`) quando você especificar um atributo. Além disso, após um maior-sinal (`>`) quando você especificar um atributo. No entanto, você deve incluir um caractere de continuação de linha (_) quando você especificar atributos de nível de assembly ou módulo.|[!code-vb[VbVbalrLineContinuation#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_24.vb)]<br /><br /> Para obter mais informações, consulte [visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md).|  
|Antes e depois de operadores de consulta (`Aggregate`, `Distinct`, `From`, `Group By`, `Group Join`, `Join`, `Let`, `Order By`, `Select`, `Skip`, `Skip While`, `Take`, `Take While`, `Where`, `In`, `Into`, `On`, `Ascending`, e `Descending`). Não é possível interromper uma linha entre as palavras-chave de operadores de consulta que são compostas de várias palavras-chave (`Order By`, `Group Join`, `Take While`, e `Skip While`).|[!code-vb[VbVbalrLineContinuation#11](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_25.vb)]<br /><br /> Para obter mais informações, consulte [consultas](../../../visual-basic/language-reference/queries/queries.md).|  
|Após o `In` palavra-chave em um `For Each` instrução.|[!code-vb[VbVbalrLineContinuation#12](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_26.vb)]<br /><br /> Para obter mais informações, consulte [para cada um... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md).|  
|Após o `From` palavra-chave em um inicializador de coleção.|[!code-vb[VbVbalrLineContinuation#13](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_27.vb)]<br /><br /> Para obter mais informações, consulte [Inicializadores de coleção](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).|  
  
## <a name="adding-comments"></a>Adicionando comentários  
 Código-fonte não é sempre auto-explicativos, até mesmo para o programador quem a escreveu. Para ajudar a documentar seu código, portanto, a maioria dos programadores usar livre de comentários inseridos. Comentários no código podem explicar um procedimento ou uma instrução específica para qualquer pessoa que ler ou trabalhar com ela mais tarde. Visual Basic ignora comentários durante a compilação, e elas não afetam o código compilado.  
  
 As linhas de comentário começam com um apóstrofo (`'`) ou `REM` seguido por um espaço. Eles podem ser adicionados em qualquer lugar no código, exceto em uma cadeia de caracteres. Para acrescentar um comentário em uma instrução, insira um apóstrofo ou `REM` depois da instrução, seguida de comentário. Comentários também podem entrar em sua própria linha separada. O exemplo a seguir demonstra essas possibilidades.  
  
 [!code-vb[VbVbalrStatements#72](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_28.vb)]  
  
## <a name="checking-compilation-errors"></a>Verificação de erros de compilação  
 Se, depois que você digitar uma linha de código, a linha é exibida com um sublinhado ondulado azul (uma mensagem de erro pode aparecer também), há um erro de sintaxe na instrução. Você deve descobrir o que há de errado com a instrução (por procurando na lista de tarefas, ou passar o mouse sobre o erro com o ponteiro do mouse e ler a mensagem de erro) e corrigi-lo. Até que você corrigir todos os erros de sintaxe em seu código, o programa não será compilado corretamente.  
  
## <a name="related-sections"></a>Seções relacionadas  
  
|Termo|Definição|  
|---|---|  
|[Operadores de Atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)|Fornece links para páginas de referência de linguagem, como operadores de atribuição de cobertura `=`, `*=`, e `&=`.|  
|[Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)|Mostra como combinar elementos com operadores para gerar novos valores.|  
|[Como quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|Mostra como dividir uma única instrução em várias linhas e como colocar várias instruções na mesma linha.|  
|[Como rotular instruções](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|Mostra como uma linha de código do rótulo.|
