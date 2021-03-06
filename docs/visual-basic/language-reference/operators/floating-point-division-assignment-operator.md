---
title: /=, opérateur (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: 642307bc531e7d9ce21a932b112795b35e7b3182
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604092"
---
# <a name="-operator-visual-basic"></a>/=, opérateur (Visual Basic)
Divise la valeur d’une variable ou une propriété par la valeur d’une expression et assigne le résultat à virgule flottante à cette variable ou propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a>Composants  
 `variableorproperty`  
 Obligatoire. Toute variable ou propriété numérique.  
  
 `expression`  
 Obligatoire. Toute expression numérique.  
  
## <a name="remarks"></a>Notes  
 L’élément sur le côté gauche de la `/=` opérateur peut être une simple variable scalaire, une propriété ou un élément d’un tableau. La variable ou la propriété ne peut pas être [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 Le `/=` opérateur divise d’abord la valeur de la variable ou propriété (sur le côté gauche de l’opérateur) par la valeur de l’expression (sur le côté droit de l’opérateur). L’opérateur assigne ensuite le résultat à virgule flottante de cette opération à la variable ou propriété.  
  
 Cette instruction assigne un `Double` valeur à la variable ou propriété sur la gauche. Si `Option Strict` est `On`, `variableorproperty` doit être un `Double`. Si `Option Strict` est `Off`, Visual Basic exécute une conversion implicite et assigne le résultat à `variableorproperty`, avec une erreur possible au moment de l’exécution. Pour plus d’informations, consultez [Conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) et [Option Strict, instruction](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="overloading"></a>Surcharge  
 Le [/, opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure. La surcharge la `/` opérateur affecte le comportement de la `/=` opérateur. Si votre code utilise `/=` sur une classe ou structure qui surcharge `/`, assurez-vous que vous comprenez son comportement redéfini. Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `/=` opérateur pour diviser une `Integer` variable par une autre et assigner le quotient à la première variable.  
  
 [!code-vb[VbVbalrOperators#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [/, Opérateur (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)  
 [\\=, Opérateur](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [Opérateurs d’assignation](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Opérateurs arithmétiques](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Instructions](../../../visual-basic/programming-guide/language-features/statements.md)
