---
title: "Optimisation des performances : graphiques 2D et acquisition d'images"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], performance
- drawing [WPF], optimizing performance
- imaging [WPF], optimizing performance
- shapes [WPF], optimizing performance
- 2-D graphics [WPF]
- images [WPF], optimizing performance
ms.assetid: e335601e-28c8-4d64-ba27-778fffd55f72
ms.openlocfilehash: 4e6b72dae863e89d70ec70c2cb99a5874581e9ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549099"
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>Optimisation des performances : graphiques 2D et acquisition d'images
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit une large gamme de fonctionnalités graphiques 2D et d’acquisition d’images qui peuvent être optimisées pour répondre aux spécifications de votre application. Cette rubrique fournit des informations sur l’optimisation des performances dans ces domaines.  
  
  
<a name="Drawing_and_Shapes"></a>   
## <a name="drawing-and-shapes"></a>Dessin et formes  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit les deux <xref:System.Windows.Media.Drawing> et <xref:System.Windows.Shapes.Shape> objets pour représenter le contenu de dessin graphique. Toutefois, <xref:System.Windows.Media.Drawing> les objets sont des constructions plus simples que <xref:System.Windows.Shapes.Shape> des objets et fournir de meilleures caractéristiques de performances.  
  
 A <xref:System.Windows.Shapes.Shape> vous permet de dessiner une forme de graphique à l’écran. Puisqu’ils sont dérivés de la <xref:System.Windows.FrameworkElement> (classe), <xref:System.Windows.Shapes.Shape> objets peuvent être utilisés à l’intérieur de panneaux et de la plupart des contrôles.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] offre plusieurs couches d’accès aux services graphiques et de rendu. À la couche supérieure, <xref:System.Windows.Shapes.Shape> les objets sont faciles à utiliser et fournissent de nombreuses fonctionnalités utiles, telles que la disposition et la gestion des événements. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit un certain nombre d’objets de forme prêts à l’emploi. Tous les objets de forme héritent la <xref:System.Windows.Shapes.Shape> classe. Objets de forme disponibles incluent <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, et <xref:System.Windows.Shapes.Rectangle>.  
  
 <xref:System.Windows.Media.Drawing> objets, en revanche, ne dérivent pas de la <xref:System.Windows.FrameworkElement> classe et fournir une implémentation légère pour le rendu des formes, des images et texte.  
  
 Il existe quatre types de <xref:System.Windows.Media.Drawing> objets :  
  
-   <xref:System.Windows.Media.GeometryDrawing> Dessine une forme.  
  
-   <xref:System.Windows.Media.ImageDrawing> Dessine une image.  
  
-   <xref:System.Windows.Media.GlyphRunDrawing> Dessine du texte.  
  
-   <xref:System.Windows.Media.DrawingGroup> Dessine d’autres dessins. Utilisez un groupe de dessins pour faire de plusieurs dessins un seul et même dessin composite.  
  
 Le <xref:System.Windows.Media.GeometryDrawing> objet est utilisé pour restituer le contenu de la géométrie. Le <xref:System.Windows.Media.Geometry> classe et les classes concrètes qui en dérivent, telles que <xref:System.Windows.Media.CombinedGeometry>, <xref:System.Windows.Media.EllipseGeometry>, et <xref:System.Windows.Media.PathGeometry>, fournissent un moyen de rendu des graphiques 2D, ainsi que fournissant le test de positionnement et la prise en charge de l’extrait. Les objets géométriques peuvent être utilisés pour définir la zone d’un contrôle, par exemple, ou pour définir la zone de détourage à appliquer à une image. Les objets géométriques peuvent être des zones simples, telles que des rectangles et des cercles, ou des zones composites créées à partir d’au moins deux objets géométriques. Zones géométriques plus complexes peuvent être créés en combinant <xref:System.Windows.Media.PathSegment>-dérivés des objets, telles que <xref:System.Windows.Media.ArcSegment>, <xref:System.Windows.Media.BezierSegment>, et <xref:System.Windows.Media.QuadraticBezierSegment>.  
  
 Sur la surface, le <xref:System.Windows.Media.Geometry> classe et le <xref:System.Windows.Shapes.Shape> sont assez semblables. Les deux sont utilisés dans le rendu des graphiques 2D et ont tous deux des classes concrètes semblables qui dérivent d’elles, par exemple, <xref:System.Windows.Media.EllipseGeometry> et <xref:System.Windows.Shapes.Ellipse>. Cependant, il existe des différences importantes entre ces deux ensembles de classes. Pour un, le <xref:System.Windows.Media.Geometry> classe ne possède pas certaines des fonctionnalités de la <xref:System.Windows.Shapes.Shape> (classe), telles que la capacité à dessiner lui-même. Pour dessiner un objet géométrique, une autre classe telle que DrawingContext, Drawing ou Path (il est important de noter que Path est une forme) doit être utilisée pour effectuer l’opération de dessin. Les propriétés de rendu telles que le remplissage, le trait et l’épaisseur de trait appartiennent à la classe qui dessine l’objet géométrique, alors qu’un objet de forme contient ces propriétés. Une façon de se figurer cette différence est de considérer qu’un objet géométrique définit une zone, par exemple un cercle, alors qu’un objet de forme définit une zone, définit son remplissage et son contour et participe au système de disposition.  
  
 Étant donné que <xref:System.Windows.Shapes.Shape> objets dérivent de la <xref:System.Windows.FrameworkElement> (classe), leur utilisation peut ajouter plus de manière significative la consommation de mémoire dans votre application. Si vous ne devez pas réellement le <xref:System.Windows.FrameworkElement> fonctionnalités pour votre contenu graphique, envisagez d’utiliser des allégés <xref:System.Windows.Media.Drawing> objets.  
  
 Pour plus d’informations sur <xref:System.Windows.Media.Drawing> , consultez [vue d’ensemble des objets de dessin](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
<a name="StreamGeometry_Objects"></a>   
## <a name="streamgeometry-objects"></a>Objets StreamGeometry  
 Le <xref:System.Windows.Media.StreamGeometry> objet est une alternative légère à <xref:System.Windows.Media.PathGeometry> pour créer des formes géométriques. Utilisez un <xref:System.Windows.Media.StreamGeometry> lorsque vous devez décrire une géométrie complexe. <xref:System.Windows.Media.StreamGeometry> est optimisé pour gérer de nombreux <xref:System.Windows.Media.PathGeometry> objets et fonctionne mieux quand elle est comparée à l’utilisation de nombreux <xref:System.Windows.Media.PathGeometry> objets.  
  
 L’exemple suivant utilise la syntaxe d’attribut pour créer un triangulaire <xref:System.Windows.Media.StreamGeometry> dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 Pour plus d’informations sur <xref:System.Windows.Media.StreamGeometry> , consultez [création d’une forme à l’aide d’un StreamGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md).  
  
<a name="DrawingVisual_Objects"></a>   
## <a name="drawingvisual-objects"></a>Objets DrawingVisual  
 Le <xref:System.Windows.Media.DrawingVisual> objet est une classe qui est utilisé pour restituer le texte, des images ou des formes de dessin légère. Cette classe est dite légère, car elle n’assure pas la gestion des dispositions ni des événements, ce qui améliore ses performances. C’est pourquoi, les dessins de ce type sont idéaux pour les arrière-plans et les images clipart. Pour plus d’informations, consultez [Utilisation d’objets DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md).  
  
<a name="Images"></a>   
## <a name="images"></a>Images  
 L’acquisition d’images [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] apporte une amélioration importante par rapport aux fonctionnalités liées aux images des précédentes de versions de [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]. Les fonctionnalités liées aux images, telles que l’affichage d’une image bitmap ou l’utilisation d’une image sur un contrôle commun, étaient principalement gérées par l’interface de programmation d’application (API) Microsoft Windows Graphics Device Interface (GDI) ou Microsoft Windows GDI+. Si ces API proposaient des fonctionnalités de base en matière d’images, elles étaient dépourvues de certaines autres fonctionnalités telles que la prise en charge de l’extensibilité de codec et des images haute fidélité. Les API d’acquisition d’images WPF ont été repensées pour surmonter les lacunes de GDI et GDI+, et proposent un nouvel ensemble d’API pour afficher et utiliser des images dans vos applications.  
  
 Quand vous utilisez des images, tenez compte des recommandations suivantes pour obtenir de meilleures performances :  
  
-   Si votre application vous impose d’afficher des images miniatures, envisagez de créer une version de taille réduite de l’image. Par défaut, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] charge votre image et la décode à sa taille maximale. Si vous voulez seulement une version miniature de l’image, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] décode inutilement l’image à sa taille maximale et la réduit ensuite à une taille miniature. Pour éviter ce traitement inutile, vous pouvez soit demander à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de décoder l’image en taille miniature, soit demander à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de charger une image de taille miniature.  
  
-   Décodez toujours l’image à la taille souhaitée et non à la taille par défaut. Comme indiqué ci-dessus, demandez à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de décoder votre image à la taille souhaitée et non à la taille maximale par défaut. Vous réduirez non seulement la plage de travail de votre application, mais son exécution sera également plus rapide.  
  
-   Si possible, combinez plusieurs images pour en faire une seule, comme une bande de film composée de plusieurs images.  
  
-   Pour plus d’informations, consultez [Vue d’ensemble de la création d’images](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).  
  
### <a name="bitmapscalingmode"></a>BitmapScalingMode  
 Quand vous animez l’échelle d’une image bitmap, l’algorithme de rééchantillonnage d’image haute qualité par défaut peut parfois consommer une quantité de ressources système telle que la fréquence d’images se dégrade et les animations deviennent saccadées. En définissant le <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A> propriété de la <xref:System.Windows.Media.RenderOptions> objet <xref:System.Windows.Media.BitmapScalingMode.LowQuality> vous pouvez créer une animation plus lisse lors de la mise à l’échelle d’une image bitmap. <xref:System.Windows.Media.BitmapScalingMode.LowQuality> Indique le mode du [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] moteur de rendu pour basculer d’un algorithme optimisé de qualité à un algorithme optimisé de vitesse lors du traitement d’images.  
  
 L’exemple suivant montre comment définir la <xref:System.Windows.Media.BitmapScalingMode> pour un objet image.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>CachingHint  
 Par défaut, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ne met pas en cache le contenu rendu des <xref:System.Windows.Media.TileBrush> objets, tels que <xref:System.Windows.Media.DrawingBrush> et <xref:System.Windows.Media.VisualBrush>. Dans les scénarios statiques où ni le contenu ni l’utilisation de la <xref:System.Windows.Media.TileBrush> dans la modification de la scène, en ce sens, puisqu’il conserve la mémoire vidéo. Il ne fait pas moins de sens lorsqu’un <xref:System.Windows.Media.TileBrush> avec un contenu statique est utilisé de façon non statique, par exemple, lorsqu’une page <xref:System.Windows.Media.DrawingBrush> ou <xref:System.Windows.Media.VisualBrush> est mappé à la surface d’un objet de la rotation 3D. Le comportement par défaut de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] consiste à restituer de nouveau l’ensemble du contenu de la <xref:System.Windows.Media.DrawingBrush> ou <xref:System.Windows.Media.VisualBrush> pour chaque image, même si le contenu est invariable.  
  
 En définissant le <xref:System.Windows.Media.RenderOptions.CachingHint%2A> propriété de la <xref:System.Windows.Media.RenderOptions> objet <xref:System.Windows.Media.CachingHint.Cache> vous pouvez augmenter les performances à l’aide des versions mises en cache des objets brush en mosaïque.  
  
 Le <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> et <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> les valeurs de propriété sont des valeurs de taille relative qui déterminent quand le <xref:System.Windows.Media.TileBrush> objet doit être régénéré en raison de modifications de l’échelle. Par exemple, en définissant le <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A> propriété 2.0, le cache pour le <xref:System.Windows.Media.TileBrush> ne doit être régénéré lorsque sa taille dépasse deux fois la taille du cache actuel.  
  
 L’exemple suivant montre comment utiliser l’option d’indicateur de mise en cache pour un <xref:System.Windows.Media.DrawingBrush>.  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet3)]
 [!code-vb[RenderOptions#RenderOptionsSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet3)]  
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des performances des applications WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Planification des performances des applications](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Tirer parti du matériel](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Disposition et conception](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Comportement de l’objet](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Ressources d'application](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Liaison de données](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Autres recommandations relatives aux performances](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
 [Conseils et astuces sur les animations](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)
