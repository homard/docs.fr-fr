---
title: Ajouter du contenu à une zone de texte à l'aide d'UI Automation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 7c4772d36a88dfede04f7592c1cab776ddcd7d7d
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47862456"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a>Ajouter du contenu à une zone de texte à l'aide d'UI Automation
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour plus d’informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [Windows Automation API : UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique contient des exemples de code qui montre comment utiliser [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour insérer du texte dans une zone de texte à ligne unique. Une autre méthode est fournie pour les contrôles de texte enrichi et multilignes où [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] n’est pas applicable. À des fins de comparaison, l’exemple montre également comment utiliser les méthodes Win32 pour obtenir les mêmes résultats.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant parcourt une séquence de contrôles de texte dans une application cible. Chaque contrôle de texte est testé pour voir si un <xref:System.Windows.Automation.ValuePattern> objet peut être obtenu à partir de celui-ci à l’aide de la <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> (méthode). Si le contrôle de texte ne prend pas en charge <xref:System.Windows.Automation.ValuePattern>, le <xref:System.Windows.Automation.ValuePattern.SetValue%2A> méthode est utilisée pour insérer une chaîne définie par l’utilisateur dans le contrôle de texte. Sinon, le <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> méthode est utilisée.  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de texte TextPattern Insert](https://msdn.microsoft.com/library/67353f93-7ee2-42f2-ab76-5c078cf6ca16)
