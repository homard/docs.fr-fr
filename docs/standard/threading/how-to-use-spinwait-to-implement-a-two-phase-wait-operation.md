---
title: "Comment : utiliser SpinWait pour implémenter une opération d'attente en deux phases"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dcb2fbf5e0a310156fdc6fac5fe736692e8ec133
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44209210"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a>Comment : utiliser SpinWait pour implémenter une opération d'attente en deux phases
L’exemple suivant montre comment utiliser un objet <xref:System.Threading.SpinWait?displayProperty=nameWithType> pour implémenter une opération d’attente en deux phases. Durant la première phase, l’objet de synchronisation (`Latch`) tourne pendant quelques cycles, le temps de vérifier si le verrou est disponible. Durant la deuxième phase, si le verrou est enfin disponible, la méthode `Wait` est retournée sans utiliser le <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> pour exécuter son attente. Dans le cas contraire, `Wait` exécute l’attente.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre une implémentation de base d’une primitive de synchronisation de verrou. Vous pouvez utiliser cette structure de données quand les temps d’attente sont supposés être très courts. L’exemple est uniquement fourni à des fins de démonstration. Si vous avez besoin d’une fonctionnalité de type verrou dans votre programme, optez pour l’utilisation de <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 Le verrou utilise l’objet <xref:System.Threading.SpinWait> pour tourner sur place uniquement jusqu’à ce que le prochain appel à `SpinOnce` provoque la transmission de la tranche horaire du thread par le <xref:System.Threading.SpinWait>. À ce stade, le verrou provoque son propre changement de contexte en appelant <xref:System.Threading.WaitHandle.WaitOne%2A> sur le <xref:System.Threading.ManualResetEvent> et en passant le reste de la valeur de délai d’attente.  
  
 La sortie de la journalisation indique la fréquence à laquelle le verrou a pu augmenter les performances en acquérant le verrou sans utiliser <xref:System.Threading.ManualResetEvent>.  
  
## <a name="see-also"></a>Voir aussi

- [SpinWait](../../../docs/standard/threading/spinwait.md)  
- [Fonctionnalités et objets de threading](../../../docs/standard/threading/threading-objects-and-features.md)
