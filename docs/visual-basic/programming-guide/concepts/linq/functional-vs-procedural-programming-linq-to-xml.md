---
title: Comparaison entre la programmation fonctionnelle Programmation procédurale (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ea1015a5-d4c8-4d79-8e1e-ba17a40a4f39
ms.openlocfilehash: 55f1e354f71e58c3592f91e198925c0fd5f0da71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643677"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-visual-basic"></a>Comparaison entre la programmation fonctionnelle Programmation procédurale (LINQ to XML) (Visual Basic)
Il existe différents types d'applications XML :  
  
-   Certaines applications prennent des documents XML sources et produisent de nouveaux documents XML d'une forme différente des documents sources.  
  
-   Certaines applications prennent des documents XML sources et produisent des documents d'une forme totalement différente, tels que des fichiers texte CSV ou HTML.  
  
-   Certaines applications prennent des documents XML sources et insèrent des enregistrements dans une base de données.  
  
-   Certaines applications prennent des données à partir d'une autre source, telle qu'une base de données, et créent des documents XML à partir de celle-ci.  
  
 Il existe d'autres types d'applications XML, mais ceux-ci sont représentatifs des types de fonctionnalités qu'un programmateur XML doit implémenter.  
  
 Avec tous ces types d'applications, un développeur peut suivre deux approches contrastées :  
  
-   Construction fonctionnelle à l'aide d'une approche déclarative.  
  
-   Modification d'arborescence XML en mémoire à l'aide de procédures de code.  
  
 LINQ to XML prend en charge les deux approches.  
  
 Lors de l'utilisation de l'approche fonctionnelle, vous écrivez des transformations qui prennent les documents sources et génèrent des documents de résultats complètement nouveaux de la forme souhaitée.  
  
 Lors de la modification d'une arborescence XML en place, vous écrivez du code qui traverse et parcourt les nœuds d'une arborescence XML en mémoire, en insérant, supprimant et modifiant des nœuds si nécessaire.  
  
 Vous pouvez utiliser LINQ to XML avec l'une ou l'autre de ces approches. Vous utilisez les mêmes classes et, dans certains cas, les mêmes méthodes. Toutefois, la structure et les objectifs des deux approches sont très différents. Par exemple, dans différentes situations, l'une ou l'autre approche fournira souvent de meilleures performances et utilisera plus ou moins de mémoire. En outre, l'une ou l'autre approche sera plus facile à écrire et génèrera du code plus facile à maintenir.  
  
 Pour voir une comparaison de ces deux approches, consultez [Comparaison de la modification d’arborescence XML en mémoire et de la Construction fonctionnelle (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md).  
  
 Pour un didacticiel sur l’écriture des transformations fonctionnelles, consultez [Pure Functional Transformations of XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ à la vue d’ensemble de programmation XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
