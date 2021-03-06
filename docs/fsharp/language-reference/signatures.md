---
title: Assinaturas (F#)
description: 'Saiba como usar um arquivo de assinatura do F # para manter informações sobre as assinaturas públicas de um conjunto de F # elementos do programa, como módulos, tipos e namespaces.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: c98ac6c62fdcee51532a162596e99309a31802ec
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="signatures"></a>Assinaturas

Um arquivo de assinatura contém informações sobre as assinaturas públicas de um conjunto de elementos de programação de F#, como tipos, namespaces e módulos. Ele pode ser usado para especificar a acessibilidade desses elementos de programa.


## <a name="remarks"></a>Comentários
Para cada arquivo de código F #, você pode ter um *arquivo de assinatura*, que é um arquivo que tem o mesmo nome que o arquivo de código, mas com o. FSI de extensão em vez de. FS. Arquivos de assinatura também podem ser adicionados à compilação de linha de comando se você estiver usando a linha de comando diretamente. Para fazer a distinção entre arquivos de código e arquivos de assinatura, arquivos de código são às vezes chamados de *arquivos de implementação*. Em um projeto, o arquivo de assinatura deve preceder o arquivo de código associado.

Um arquivo de assinatura descreve os namespaces, módulos, tipos e membros no arquivo de implementação correspondente. Use as informações em um arquivo de assinatura para especificar quais partes do código na implementação correspondente de arquivo pode ser acessado pelo código fora do arquivo de implementação e quais partes são internos para o arquivo de implementação. Os namespaces, módulos e tipos que são incluídos no arquivo de assinatura devem ser um subconjunto dos namespaces, módulos e tipos que são incluídos no arquivo de implementação. Com algumas exceções indicadas neste tópico, os elementos de linguagem que não estão listados no arquivo de assinatura são considerados particulares para o arquivo de implementação. Se nenhum arquivo de assinatura for encontrado no projeto ou na linha de comando, a acessibilidade padrão será usada.

Para obter mais informações sobre a acessibilidade padrão, consulte [controle de acesso](access-control.md).

Em um arquivo de assinatura, você não se repetem a definição dos tipos e as implementações de cada método ou função. Em vez disso, use a assinatura para cada método e a função, que atua como uma especificação completa da funcionalidade que é implementada por um fragmento de namespace ou módulo. A sintaxe para uma assinatura de tipo é a mesma usada em declarações de método abstract em interfaces e classes abstratas e também é mostrada a IntelliSense e o fsi.exe interpretador F # quando ele for exibido entrada compilada corretamente.

Se não há informações suficientes na assinatura de tipo para indicar se um tipo é lacrado, ou se é um tipo de interface, você deve adicionar um atributo que indica a natureza do tipo para o compilador. Atributos que você pode usar para essa finalidade são descritos na tabela a seguir.



|Atributo|Descrição|
|---------|-----------|
|`[<Sealed>]`|Para um tipo que não tem nenhum membro abstrato ou que não deve ser estendido.|
|`[<Interface>]`|Para um tipo que é uma interface.|
O compilador gera um erro se os atributos não são consistentes entre a assinatura e a declaração no arquivo de implementação.

Use a palavra-chave `val` para criar uma assinatura para um valor ou o valor da função. A palavra-chave `type` apresenta uma assinatura de tipo.

Você pode gerar um arquivo de assinatura usando o `--sig` opção de compilador. Em geral, você não gravar arquivos. FSI manualmente. Em vez disso, você gerar arquivos. FSI, usando o compilador, adicioná-los ao seu projeto, se você tiver um e editá-los, removendo os métodos e as funções que você não deseja ser acessível.

Há várias regras para assinaturas de tipo:


- Abreviações de tipo em um arquivo de implementação não devem corresponder a um tipo sem uma abreviação em um arquivo de assinatura.


- Registros e uniões discriminadas devem expor todos ou nenhum de seus campos e construtores, e a ordem em que a assinatura deve corresponder à ordem em que o arquivo de implementação. Classes podem revelar alguns, todos ou nenhum de seus campos e métodos na assinatura.


- Classes e estruturas que tenham construtores devem expor as declarações de suas classes base (o `inherits` declaração). Além disso, classes e estruturas que tenham construtores devem expor todos os métodos abstratos e declarações de interface.


- Tipos de interface devem revelar todos os seus métodos e interfaces.


As regras para assinaturas de valor são da seguinte maneira:


- Modificadores de acessibilidade (`public`, `internal`, e assim por diante) e o `inline` e `mutable` modificadores na assinatura devem corresponder na implementação.


- O número de parâmetros de tipo genérico (ou inferido implicitamente ou explicitamente declarado) deve corresponder e os tipos e as restrições de tipo em parâmetros de tipo genérico devem corresponder.


- Se o `Literal` atributo é usado, ele deverá aparecer na assinatura e a implementação e o mesmo valor literal deve ser usado para ambos.


- O padrão de parâmetros (também conhecido como o *arity*) de assinaturas e implementações devem ser consistentes.


O exemplo de código a seguir mostra um exemplo de um arquivo de assinatura que tem o namespace, módulo, valor da função e as assinaturas de tipo junto com os atributos apropriados. Ele também mostra o arquivo de implementação correspondente.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9002.fs)]

O código a seguir mostra o arquivo de implementação.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9001.fs)]
    
## <a name="see-also"></a>Consulte também
[Referência da Linguagem F#](index.md)

[Controle de Acesso](access-control.md)

[Opções do Compilador](compiler-options.md)
