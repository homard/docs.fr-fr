---
title: Gestion des exceptions (F#)
description: 'Découvrez les principes fondamentaux de la gestion des exceptions dans F # et des liens vers des expressions et des fonctions de gestion des exceptions.'
ms.date: 05/16/2016
ms.openlocfilehash: fc89feb0d21bc823cb105e435413f8309cd6174c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564324"
---
# <a name="exception-handling"></a>Gestion des exceptions

Cette section contient des informations sur la prise en charge de la gestion des exceptions en langage F#.


## <a name="exception-handling-basics"></a>Concepts de base de la gestion des exceptions
La gestion des exceptions constitue le moyen standard de gérer les conditions d’erreur dans le .NET Framework. Par conséquent, tout langage .NET doit prendre en charge ce mécanisme, notamment F#. Une *exception* est un objet qui encapsule des informations sur une erreur. Quand des erreurs se produisent, des exceptions sont déclenchées et l’exécution normale s’arrête. Le runtime recherche alors un gestionnaire approprié pour l’exception. La recherche démarre dans la fonction active et remonte dans la pile en passant par les couches d’appelants jusqu’à ce qu’un gestionnaire correspondant soit trouvé. Le gestionnaire est ensuite exécuté.

De plus, à mesure que la pile est déroulée, le runtime exécute le code présent dans les blocs `finally` pour garantir que les objets sont nettoyés correctement pendant le processus de déroulement.


## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----|-----------|
|[Types d'exceptions](exception-types.md)|Décrit comment déclarer un type d’exception.|
|[Exceptions : expression `try...with`](the-try-with-expression.md)|Décrit la construction de langage qui prend en charge la gestion des exceptions.|
|[Exceptions : expression `try...finally`](the-try-finally-expression.md)|Décrit la construction de langage qui vous permet d’exécuter du code de nettoyage à mesure que la pile se déroule quand une exception est levée.|
|[Exceptions : fonction `raise`](the-raise-Function.md)|Décrit comment lever un objet exception.|
|[Exceptions : fonction `failwith`](the-failwith-function.md)|Décrit comment générer une exception F# générale.|
|[Exceptions : fonction `invalidArg`](the-invalidArg-function.md)|Décrit comment générer une exception d’argument non valide.|
