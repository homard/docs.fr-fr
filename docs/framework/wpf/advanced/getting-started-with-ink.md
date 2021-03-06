---
title: Créer un InkCanvas dans une application WPF dans Visual Studio
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- XAML [WPF], procedural code in lieu of
- InkCanvas (WPF)
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
ms.openlocfilehash: 600d8528125606c6e1af5b031e2fc31aabb79206
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925042"
---
# <a name="get-started-with-ink-in-wpf"></a>Bien démarrer avec l’encre dans WPF

Windows Presentation Foundation (WPF) possède une fonctionnalité de l’encre qui permet de facilement incorporer l’encre numérique dans votre application.

## <a name="prerequisites"></a>Prérequis

Pour utiliser les exemples suivants, tout d’abord [installer Microsoft Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017). Cela permet également de savoir comment écrire des applications WPF de base. Pour bien démarrer avec WPF, consultez [procédure pas à pas : Ma première application de bureau WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).

## <a name="quick-start"></a>Guide de démarrage rapide

Cette section vous permet d’écrire une application WPF simple qui collecte d’encre.

### <a name="got-ink"></a>Vous avez l’encre ?

Pour créer une application WPF qui prend en charge de l’encre :

1. Ouvrez Visual Studio.

2. Créer un nouveau **application WPF**.

   Dans le **nouveau projet** boîte de dialogue, développez le **installé** > **Visual C#** ou **Visual Basic**  >   **Windows Desktop** catégorie. Ensuite, sélectionnez le **application WPF (.NET Framework)** modèle d’application. Entrez un nom, puis sélectionnez **OK**.

   Visual Studio crée le projet, et *MainWindow.xaml* s’ouvre dans le concepteur.

3. Type `<InkCanvas/>` entre le `<Grid>` balises.

   ![Concepteur XAML avec la balise de InkCanvas](media/getting-started-with-ink/inkcanvas-xaml.png)

4. Appuyez sur **F5** pour lancer votre application dans le débogueur.

5. À l’aide d’un stylet ou une souris, écrire **Bonjour** dans la fenêtre.

Vous avez écrit l’équivalent de l’encre d’une application « hello world » avec des séquences de touches que 12 !

### <a name="spice-up-your-app"></a>Pimenter votre application

Tirez parti de certaines fonctionnalités de WPF. Remplacez tous les éléments entre les balises \<fenêtre > balises par le balisage suivant :

```xaml
<Page>
  <InkCanvas Name="myInkCanvas" MouseRightButtonUp="RightMouseUpHandler">
    <InkCanvas.Background>
      <LinearGradientBrush>
        <GradientStop Color="Yellow" Offset="0.0" />
          <GradientStop Color="Blue" Offset="0.5" />
            <GradientStop Color="HotPink" Offset="1.0" />
              </LinearGradientBrush>
    </InkCanvas.Background>
  </InkCanvas>
</Page>
```

Ce XAML crée un arrière-plan de pinceau de dégradé sur votre surface d’entrée manuscrite.

![Couleurs de dégradé sur l’écriture manuscrite surface dans une application WPF](media/getting-started-with-ink/gradient-colors.png)

### <a name="add-some-code-behind-the-xaml"></a>Ajouter du Code derrière le XAML

Bien que XAML rend très facile de concevoir l’interface utilisateur, n’importe quelle application réelle doit ajouter du code pour gérer les événements. Voici un exemple simple qui se concentre sur l’encre en réponse à un clic droit de la souris.

1. Définir le `MouseRightButtonUp` gestionnaire dans votre XAML :

   [!code-xaml[DigitalInkTopics#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]

1. Dans **l’Explorateur de solutions**, développez MainWindow.xaml et ouvrez le fichier code-behind (MainWindow.xaml.cs ou MainWindow.xaml.vb). Ajoutez le code de gestionnaire d’événements suivantes :

   [!code-csharp[DigitalInkTopics#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
   [!code-vb[DigitalInkTopics#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]

1. Exécutez l'application. Ajouter du contenu de texte, puis le bouton droit de la souris ou effectuer un équivalent d’appuyer et maintenir un stylet.

   L’affichage effectue un zoom avant dans chaque fois que vous cliquez avec le bouton droit de la souris.

### <a name="use-procedural-code-instead-of-xaml"></a>Utiliser du Code procédural au lieu de XAML

Vous pouvez accéder à toutes les fonctionnalités WPF à partir de code procédural. Suivez ces étapes pour créer une application « Hello Ink World » pour WPF qui n’utilise pas n’importe quel XAML du tout.

1. Créer un nouveau projet d’application console dans Visual Studio.

   Dans le **nouveau projet** boîte de dialogue, développez le **installé** > **Visual C#** ou **Visual Basic**  >   **Windows Desktop** catégorie. Ensuite, sélectionnez le **application Console (.NET Framework)** modèle d’application. Entrez un nom, puis sélectionnez **OK**.

1. Collez le code suivant dans le fichier Program.cs ou Program.vb :

   [!code-csharp[InkCanvasConsoleApp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
   [!code-vb[InkCanvasConsoleApp#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]

1. Ajouter des références aux assemblys PresentationCore, PresentationFramework et WindowsBase en cliquant sur **références** dans **l’Explorateur de solutions** et en choisissant **ajouter une référence**.

   ![Gestionnaire de références montrant PresentationCore et PresentationFramework](media/getting-started-with-ink/references.png)

1. Générez l’application en appuyant sur **F5**.

## <a name="see-also"></a>Voir aussi

- [Encre numérique](../../../../docs/framework/wpf/advanced/digital-ink.md)
- [Collecte d'encre](../../../../docs/framework/wpf/advanced/collecting-ink.md)
- [Reconnaissance d'écriture manuscrite](../../../../docs/framework/wpf/advanced/handwriting-recognition.md)
- [Stockage de l’encre](../../../../docs/framework/wpf/advanced/storing-ink.md)
