---
title: "UI Automation Support for the Pane Control Type | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "UI Automation, Pane control type"
  - "Pane control type"
  - "control types, Pane"
ms.assetid: 79761191-4449-4630-899c-9cbdb8867d3f
caps.latest.revision: 25
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 25
---
# UI Automation Support for the Pane Control Type
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique fournit des informations sur la prise en charge d’[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pour le type de contrôle Pane. Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], un type de contrôle est un ensemble de conditions qu’un contrôle doit respecter pour pouvoir utiliser la propriété <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>. Les conditions incluent des recommandations spécifiques pour l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], les valeurs de propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] et les modèles de contrôle.  
  
 Le type de contrôle Pane permet de représenter un objet dans un frame ou une fenêtre de document. Les utilisateurs peuvent naviguer entre des contrôles de volet et au sein du contenu du volet actif, mais ils ne peuvent pas naviguer entre des éléments de volets différents. Par conséquent, les contrôles de volet représentent un niveau de regroupement inférieur aux fenêtres et aux documents, mais supérieur aux contrôles individuels. L’utilisateur navigue entre les volets en appuyant sur TAB, F6 ou Ctrl\+Tab, en fonction du contexte. Aucune navigation spécifique au clavier n’est requise par le type de contrôle Pane.  
  
 Les sections suivantes définissent l’arborescence, les propriétés, les modèles de contrôle et les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requis pour le type de contrôle Pane. Les exigences [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] s’appliquent à tous les contrôles de liste, qu’il s’agisse de [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] ou [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## Arborescence UI Automation requise  
 Le tableau suivant illustre la vue de contrôle et la vue de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] relative aux contrôles de volet, et décrit ce que peut contenir chaque vue. Pour plus d’informations sur l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Vue de contrôle|Vue de contenu|  
|---------------------|--------------------|  
|Volet|Volet|  
  
<a name="Required_UI_Automation_Properties"></a>   
## Propriétés UI Automation requises  
 Le tableau suivant répertorie les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dont la valeur ou la définition est particulièrement pertinente pour les contrôles de volet. Pour plus d’informations sur les propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Valeur|Notes|  
|-------------------------------------------------------------------------------------|------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Consultez les notes.|La valeur de cette propriété doit être unique dans tous les contrôles d’une application.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Consultez les notes.|Rectangle externe qui contient l’ensemble du contrôle.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Consultez les notes.|Si le contrôle peut recevoir le focus clavier, il doit prendre en charge cette propriété.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Consultez les notes.|La valeur de cette propriété doit toujours être un titre clair, concis et explicite.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Consultez les notes.|Cette propriété expose un point interactif du contrôle de volet qui, lorsque vous cliquez dessus, place le focus sur le volet.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Consultez les notes.|Les contrôles Pane n’ont pas d’étiquette statique. S’il existe une étiquette de texte statique, il doit être exposé via cette propriété.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Volet|Cette valeur est la même pour toutes les infrastructures d’[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|« volet »|Chaîne localisée correspondant au type de contrôle Pane.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Les contrôles de volet sont toujours inclus dans la vue de contenu de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Les contrôles de volet sont toujours inclus dans la vue de contrôle de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|Le texte d’aide des contrôles de volet doit expliquer l’objectif du frame et sa relation aux autres frames. Une description est nécessaire si l’objectif et la relation des frames n’est pas clair à partir de la valeur de `NameProperty`. "|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>|Consultez les notes.|Si une combinaison de touches spécifique place le focus sur le volet, ces informations doivent être exposées via cette propriété.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## Modèles de contrôle UI Automation requis  
 Le tableau suivant répertorie les modèles de contrôle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par tous les contrôles de volet. Pour plus d’informations sur les modèles de contrôle, consultez [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Modèle de contrôle|Prise en charge|Notes|  
|------------------------|---------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider>|Selon le cas|Implémentez ce modèle de contrôle si le contrôle de volet peut être déplacé, redimensionné ou pivoté sur l’écran.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider>|Never|Si vous avez besoin d’implémenter ce modèle de contrôle, votre contrôle doit être basé sur le type de contrôle <xref:System.Windows.Automation.ControlType.Window>.|  
|<xref:System.Windows.Automation.Provider.IDockProvider>|Selon le cas|Implémentez ce modèle de contrôle si le contrôle de volet peut être ancré.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Selon le cas|Implémentez ce modèle de contrôle si le contrôle de volet peut faire l’objet d’un défilement.|  
  
<a name="Required_UI_Automation_Events"></a>   
## Événements UI Automation requis  
 Le tableau suivant répertorie les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] qui doivent être pris en charge par tous les contrôles de volet. Pour plus d’informations sur les événements, consultez [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|Événement [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Prise en charge \/ Valeur|Notes|  
|-------------------------------------------------------------------------------------|-------------------------------|-----------|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent>|Never|Aucun|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent>|Never|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AsyncContentLoadedEvent>|Obligatoire|None|  
|Événement de modification de propriété <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Obligatoire|None|  
|Événement de modification de propriété <xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Obligatoire|None|  
|Événement de modification de propriété <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>|Obligatoire|None|  
|Événement de modification de propriété <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>|Selon le cas|None|  
|Événement de modification de propriété <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>|Selon le cas|None|  
|Événement de modification de propriété <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>|Selon le cas|None|  
|Événement de modification de propriété <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>|Selon le cas|None|  
|Événement de modification de propriété <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>|Selon le cas|None|  
|Événement de modification de propriété <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>|Selon le cas|None|  
|Événement de modification de propriété <xref:System.Windows.Automation.WindowPatternIdentifiers.WindowVisualStateProperty>|Jamais|Aucun|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Obligatoire|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Obligatoire|None|  
  
<a name="Pane_Control_Type_Example"></a>   
## Exemple de type de contrôle Pane  
 L’image suivante illustre un contrôle qui implémente le type de contrôle Pane.  
  
 ![Capture d'écran : fenêtre d'applet avec deux volets](../../../docs/framework/ui-automation/media/uiauto-pane.png "uiauto\_pane")  
  
|Arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] – Vue de contrôle|Arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] – Vue de contenu|  
|----------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|  
|<ul><li>Volet</li><li>Tree \(modèle Scroll\)<br /><br /> <ul><li>TreeItem</li><li>Volet</li><li>Edit \(modèle Scroll\)</li></ul></li></ul>|-   Volet<br />-   Tree \(modèle Scroll\)<br />-   TreeItem<br />-   …Pane<br />-   Modifier<br />-   \(modèle Scroll\)|  
  
## Voir aussi  
 <xref:System.Windows.Automation.ControlType.Pane>   
 [UI Automation Control Types Overview](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)   
 [UI Automation Overview](../../../docs/framework/ui-automation/ui-automation-overview.md)