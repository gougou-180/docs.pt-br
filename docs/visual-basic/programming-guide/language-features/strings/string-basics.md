---
title: Noções básicas de cadeias de caracteres
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: 7141966e3c8a8cbce42111c56a85a00709e8fe1a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344291"
---
# <a name="string-basics-in-visual-basic"></a>Noções básicas de cadeias de caracteres no Visual Basic
O tipo de dados `String` representa uma série de caracteres (cada um representando, por sua vez, uma instância do tipo de dados `Char`). Este tópico apresenta os conceitos básicos de cadeias de caracteres no Visual Basic.  
  
## <a name="string-variables"></a>Variáveis de cadeia de caracteres  
 Uma instância de uma cadeia de caracteres pode ser atribuída a um valor literal que representa uma série de caracteres. Por exemplo:  
  
 [!code-vb[VbVbalrStrings#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#63)]  
  
 Uma variável `String` também pode aceitar qualquer expressão que seja avaliada como uma cadeia de caracteres. São mostrados exemplos abaixo:  
  
 [!code-vb[VbVbalrStrings#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#64)]  
  
 Qualquer literal atribuído a uma variável `String` deve ser colocado entre aspas (""). Isso significa que uma aspa dentro de uma cadeia de caracteres não pode ser representada por uma aspa. Por exemplo, o código a seguir causa um erro do compilador:  
  
 [!code-vb[VbVbalrStrings#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#65)]  
  
 Esse código causa um erro porque o compilador encerra a cadeia de caracteres após a segunda aspa e o restante da cadeia de caracteres é interpretado como código. Para resolver esse problema, Visual Basic interpreta duas aspas em um literal de cadeia de caracteres como uma aspa na cadeia de caracteres. O exemplo a seguir demonstra a maneira correta de incluir uma aspa em uma cadeia de caracteres:  
  
 [!code-vb[VbVbalrStrings#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#66)]  
  
 No exemplo anterior, as duas aspas anteriores à palavra `Look` se tornam uma aspa na cadeia de caracteres. As três aspas no final da linha representam uma aspa na cadeia de caracteres e no caractere de terminação da cadeia de caracteres.  
  
 Literais de cadeia de caracteres podem conter várias linhas:  
  
```vb  
Dim x = "hello  
world"  
```  
  
 A cadeia de caracteres resultante contém sequências de nova linha que você usou em seu literal de cadeia de caracteres (vbCr, vbCrLf, etc.).  Você não precisa mais usar a solução alternativa antiga:  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a>Caracteres em Strings  
 Uma cadeia de caracteres pode ser considerada como uma série de valores de `Char`, e o tipo de `String` tem funções internas que permitem executar muitas manipulações em uma cadeia de caracteres que se assemelham às manipulações permitidas por matrizes. Como todas as matrizes na .NET Framework, elas são matrizes baseadas em zero. Você pode se referir a um caractere específico em uma cadeia de caracteres por meio da propriedade `Chars`, que fornece uma maneira de acessar um caractere pela posição na qual ele aparece na cadeia de caracteres. Por exemplo:  
  
 [!code-vb[VbVbalrStrings#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#67)]  
  
 No exemplo acima, a propriedade `Chars` da cadeia de caracteres retorna o quarto caractere na cadeia de caracteres, que é `D`e o atribui a `myChar`. Você também pode obter o comprimento de uma cadeia de caracteres específica por meio da propriedade `Length`. Se você precisar executar várias manipulações de tipo de matriz em uma cadeia de caracteres, poderá convertê-la em uma matriz de instâncias de `Char` usando a função `ToCharArray` da cadeia de caracteres. Por exemplo:  
  
 [!code-vb[VbVbalrStrings#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#68)]  
  
 A variável `myArray` agora contém uma matriz de valores de `Char`, cada um representando um caractere de `myString`.  
  
## <a name="the-immutability-of-strings"></a>A imutabilidade das cadeias de caracteres  
 Uma cadeia de caracteres é *imutável*, o que significa que seu valor não pode ser alterado após ter sido criado. No entanto, isso não impede que você atribua mais de um valor a uma variável de cadeia de caracteres. Considere o exemplo a seguir:  
  
 [!code-vb[VbVbalrStrings#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#69)]  
  
 Aqui, uma variável de cadeia de caracteres é criada, dado um valor e, em seguida, seu valor é alterado.  
  
 Mais especificamente, na primeira linha, uma instância do tipo `String` é criada e recebe o valor `This string is immutable`. Na segunda linha do exemplo, uma nova instância é criada e recebe o valor `Or is it?`e a variável de cadeia de caracteres descarta sua referência à primeira instância e armazena uma referência à nova instância.  
  
 Ao contrário de outros tipos de dados intrínsecos, `String` é um tipo de referência. Quando uma variável de tipo de referência é passada como um argumento para uma função ou sub-rotina, uma referência ao endereço de memória em que os dados são armazenados é passada em vez do valor real da cadeia de caracteres. Portanto, no exemplo anterior, o nome da variável permanece o mesmo, mas aponta para uma instância nova e diferente da classe `String`, que contém o novo valor.  
  
## <a name="see-also"></a>Consulte também

- [Introdução às cadeias de caracteres no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [Tipo de Dados String](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Tipo de Dados de Caractere](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Operações básicas de cadeias de caracteres](../../../../standard/base-types/basic-string-operations.md)
