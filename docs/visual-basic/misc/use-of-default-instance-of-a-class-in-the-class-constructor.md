---
title: L’utilisation de l’instance par défaut d’une classe dans le constructeur de classe pourrait entraîner des appels récurrents infinis
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: cf5d3e16c43920a90b69c815f91601c6d33c845d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33638369"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a>L’utilisation de l’instance par défaut d’une classe dans le constructeur de classe pourrait entraîner des appels récurrents infinis
Une instance par défaut d’une classe a été utilisée dans le constructeur de la classe. Cela peut entraîner un appel récurrent infini, également appelé « boucle infinie ».  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Supprimez l’instance par défaut du constructeur de la classe.  
  
## <a name="see-also"></a>Voir aussi  
 [Constructeurs](~/docs/visual-basic/programming-guide/concepts/object-oriented-programming.md#constructors)
