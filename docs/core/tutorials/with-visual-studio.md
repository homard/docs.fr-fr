---
title: Génération d’une application Hello World avec .NET Core et C# dans Visual Studio 2017
description: Découvrez comment créer une application de console .NET Core simple avec C# à l’aide de Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 09/13/2017
ms.custom: vs-dotnet
ms.openlocfilehash: 031c0a433391fbe4cdd40f6ce648f476787baf48
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003020"
---
# <a name="build-a-c-hello-world-application-with-net-core-in-visual-studio-2017"></a>Générer une application C# Hello World avec .NET Core dans Visual Studio 2017

Cette rubrique fournit une introduction pas à pas pour la création, le débogage et la publication d’une application de console .NET Core à l’aide de C# dans Visual Studio 2017. Visual Studio 2017 fournit un environnement de développement complet pour la création d’applications .NET Core. Tant que l’application n’a pas de dépendances spécifiques à la plateforme, elle peut s’exécuter sur n’importe quelle plateforme ciblée par .NET Core et sur tout système où .NET Core est installé.

## <a name="prerequisites"></a>Prérequis

[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), avec la charge de travail « Développement multiplateforme .Net Core » installée. Vous pouvez développer votre application avec .NET Core 1.1 ou .NET Core 2.0.

Pour plus d’informations, consultez la rubrique [Configuration requise pour .NET Core sur Windows](../../core/windows-prerequisites.md).

## <a name="a-simple-hello-world-application"></a>Une application Hello World simple

Commencez par créer une application console « Hello World » simple. Procédez comme suit :

1. Lancez Visual Studio 2017. Sélectionnez **Fichier** > **Nouveau** > **Projet** dans la barre de menus. Dans la boîte de dialogue *Nouveau projet**, sélectionnez le nœud **Visual C#** suivi du nœud **.NET Core**. Ensuite, sélectionnez le modèle de projet **Application console (.NET Core)**. Dans la zone de texte **Nom**, tapez « HelloWorld ». Sélectionnez le bouton **OK**.

   ![Boîte de dialogue Nouveau projet avec Application console sélectionné](./media/with-visual-studio/newproject.png)
   
1. Visual Studio utilise le modèle pour créer votre projet. Le modèle d’application console C# pour .NET Core définit automatiquement une classe, `Program`, avec une méthode unique, `Main`, qui accepte un tableau de <xref:System.String> comme argument. `Main` est le point d’entrée de l’application. Cette méthode est appelée automatiquement par le runtime lors du lancement de l’application. Tous les arguments de ligne de commande fournis au lancement de l’application sont disponibles dans le tableau *args*.

   ![Visual Studio et le nouveau projet HelloWorld](./media/with-visual-studio/devenv.png)

   Le modèle crée une application « Hello World » simple. Il appelle la méthode <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> pour afficher la chaîne littérale « Hello World ! » dans la fenêtre de console. En sélectionnant le bouton **HelloWorld** avec la flèche verte dans la barre d’outils, vous pouvez exécuter le programme en mode débogage. Si vous le faites, la fenêtre de console est visible seulement pendant un court intervalle de temps avant sa fermeture. Cela se produit, car la méthode `Main` se termine et l’application se termine dès que l’instruction unique de la méthode `Main` s’exécute.

1. Pour que l’application se mette en pause de fermer la fenêtre de console, ajoutez le code suivant immédiatement après l’appel à la méthode <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> :

   ```csharp
   Console.Write("Press any key to continue...");
   Console.ReadKey(true);
   ```
   Ce code invite l’utilisateur à appuyer sur une touche, puis arrête le programme jusqu'à ce que l’utilisateur appuie sur une touche.

1. Dans la barre de menus, sélectionnez **Générer** > **Générer la solution**. Ceci compile votre programme en un langage intermédiaire, qui est ensuite converti en code binaire par un compilateur juste-à-temps (JIT).

1. Exécutez le programme en sélectionnant le bouton **HelloWorld** avec la flèche verte dans la barre d’outils.

   ![Fenêtre de console affichant « Hello World Press any key to continue »](./media/with-visual-studio/helloworld1.png)

1. Appuyez sur une touche pour fermer la fenêtre de console.

## <a name="enhancing-the-hello-world-application"></a>Amélioration de l’application Hello World

Améliorez votre application pour inviter l’utilisateur à entrer son nom, et pour l’afficher avec la date et l’heure. Pour modifier et tester le programme, procédez comme suit :

1. Entrez le code C# suivant dans la fenêtre de code immédiatement après le crochet ouvrant qui suit la ligne `static void Main(string[] args)` et avant le premier crochet fermant :

   [!code-csharp[GettingStarted#1](../../../samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   Ce code remplace les instructions <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType> et <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> existantes.

   ![Fichier du programme C# Visual Studio avec la méthode Main mise à jour](./media/with-visual-studio/codewindow.png)

   Ce code affiche « What is your name? ». dans la fenêtre de console et attend que l’utilisateur entre une chaîne suivie de la touche Entrée. Il stocke cette chaîne dans une variable nommée `name`. Elle récupère également la valeur de la propriété <xref:System.DateTime.Now?displayProperty=nameWithType>, qui contient l’heure locale actuelle et l’assigne à une variable nommée `date`. Enfin, elle utilise une [chaîne interpolée](../../csharp/language-reference/tokens/interpolated.md) pour afficher ces valeurs dans la fenêtre de console.

1. Recompilez le programme en choisissant **Build** > **Générer la solution**.

1. Exécutez le programme en mode débogage dans Visual Studio en sélectionnant la flèche verte dans la barre d’outils, en appuyant sur F5 ou en choisissant l’élément de menu **Déboguer** > **Démarrer le débogage**. Répondez à l’invite en entrant un nom et en appuyant sur la touche Entrée.

   ![Fenêtre de console avec la sortie du programme modifié](./media/with-visual-studio/helloworld2.png)

1. Appuyez sur une touche pour fermer la fenêtre de console.

Vous avez créé et exécuté votre application. Pour développer une application professionnelle, appliquez quelques étapes supplémentaires pour rendre votre application prête à être publiée :

- Pour plus d’informations sur le débogage de votre application, consultez [Débogage de votre application C# Hello World avec Visual Studio 2017](debugging-with-visual-studio.md).

- Pour plus d’informations sur le développement et la publication d’une version distribuable de votre application, consultez [Publication de votre application C# Hello World avec Visual Studio 2017](publishing-with-visual-studio.md).

## <a name="related-topics"></a>Rubriques connexes

Au lieu d’une application console, vous pouvez également créer une bibliothèque de classes .NET Core et Visual Studio 2017. Pour une introduction pas à pas, consultez [Génération d’une bibliothèque de classes avec C# et .NET Core dans Visual Studio 2017](library-with-visual-studio.md).

Vous pouvez également développer une application de console .NET Core sur Mac, Linux et Windows à l’aide de [Visual Studio Code](https://code.visualstudio.com/), un éditeur de code téléchargeable. Pour obtenir un didacticiel pas à pas, consultez [Bien démarrer avec Visual Studio](with-visual-studio-code.md).
