---
title: Let, clause (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 34c0fd239d9e08dab4a107cb8447941e7ab3ecbe
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516761"
---
# <a name="let-clause-visual-basic"></a>Let, clause (Visual Basic)
Calcule une valeur et l’assigne à une nouvelle variable dans la requête.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`variable`|Obligatoire. Un alias qui peut être utilisé pour référencer les résultats de l’expression fournie.|  
|`expression`|Obligatoire. Une expression qui sera évaluée et assignée à la variable spécifiée.|  
  
## <a name="remarks"></a>Notes  
 Le `Let` clause vous permet de calculer des valeurs pour chaque résultat de la requête et les référencent en utilisant un alias. L’alias peut être utilisé dans d’autres clauses, telles que le `Where` clause. Le `Let` clause vous permet de créer une instruction de requête qui est plus facile à lire, car vous pouvez spécifier un alias pour une clause d’expression incluse dans la requête et substituer l’alias chaque fois que la clause d’expression est utilisée.  
  
 Vous pouvez inclure un nombre quelconque de `variable` et `expression` attributions dans le `Let` clause. Séparez chaque affectation par une virgule (,).  
  
## <a name="example"></a>Exemple  
 Le code suivant exemple utilise le `Let` clause pour calculer une remise de 10 pour cent sur les produits.  
  
 [!code-vb[VbSimpleQuerySamples#16](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/let-clause_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Requêtes](../../../visual-basic/language-reference/queries/index.md)  
 [Select (clause)](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From (clause)](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Where (clause)](../../../visual-basic/language-reference/queries/where-clause.md)
