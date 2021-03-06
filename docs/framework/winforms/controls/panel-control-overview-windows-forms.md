---
title: Vue d'ensemble du contrôle Panel (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Panel
helpviewer_keywords:
- grouping controls [Windows Forms], Panel control
- Panel control [Windows Forms], about Panel control
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
ms.openlocfilehash: 1ba766629f923b091459531ce74d28dca4b4ea0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539340"
---
# <a name="panel-control-overview-windows-forms"></a>Vue d'ensemble du contrôle Panel (Windows Forms)
Windows Forms <xref:System.Windows.Forms.Panel> contrôles sont utilisés pour fournir un groupement identifiable pour d’autres contrôles. En règle générale, vous utilisez les panneaux pour diviser un formulaire par fonction. Par exemple, peut avoir un bon de commande qui spécifie les options de distribution telles que le lendemain à utiliser. Toutes les options dans un volet de regroupement donne à l’utilisateur une aide visuelle logique. Au moment du design tous les contrôles peuvent être déplacés facilement — lorsque vous déplacez le <xref:System.Windows.Forms.Panel> contrôler, tous ses contrôles contenus déplacent, trop. Les contrôles regroupés dans un panneau de configuration est accessible via son <xref:System.Windows.Forms.Control.Controls%2A> propriété. Cette propriété retourne une collection de <xref:System.Windows.Forms.Control> instances, donc vous devez généralement effectuer un cast d’un contrôle récupérés qu’à son type spécifique.  
  
## <a name="panel-versus-groupbox"></a>Panneau par rapport à la zone de groupe  
 Le <xref:System.Windows.Forms.Panel> contrôle est semblable à la <xref:System.Windows.Forms.GroupBox> contrôle ; Toutefois, uniquement les <xref:System.Windows.Forms.Panel> contrôle peut avoir des barres de défilement et uniquement le <xref:System.Windows.Forms.GroupBox> contrôle affiche une légende.  
  
## <a name="key-properties"></a>Principales propriétés  
 Pour afficher les barres de défilement, définissez la <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> propriété `true`. Vous pouvez également personnaliser l’apparence du panneau en définissant le <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, et <xref:System.Windows.Forms.Panel.BorderStyle%2A> propriétés. Pour plus d’informations sur la <xref:System.Windows.Forms.Control.BackColor%2A> et <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriétés, consultez [Comment : définir l’arrière-plan d’un panneau](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md). Le <xref:System.Windows.Forms.Panel.BorderStyle%2A> propriété détermine si le panneau de configuration est décrite par aucune bordure visible (<xref:System.Windows.Forms.BorderStyle.None>), une simple ligne (<xref:System.Windows.Forms.BorderStyle.FixedSingle>), ou d’une ligne ombrée (<xref:System.Windows.Forms.BorderStyle.Fixed3D>).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Panel>  
 [GroupBox, contrôle](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)  
 [Guide pratique pour grouper les contrôles avec le contrôle Panel Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)  
 [Guide pratique pour définir l'arrière-plan d'un contrôle Panel Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)
