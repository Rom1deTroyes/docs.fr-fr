---
title: 'Comment : appliquer un dessin à un modèle 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 26a84d963cac3b5c23617bfaa23279021e29c07a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559062"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>Comment : appliquer un dessin à un modèle 3D
Cet exemple montre comment utiliser un <xref:System.Windows.Media.DrawingBrush> comme le <xref:System.Windows.Media.Media3D.Material> appliqué à un [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modèle.  
  
 Le code suivant définit un <xref:System.Windows.Media.DrawingGroup> comme contenu d’un <xref:System.Windows.Media.DrawingBrush>.  Le <xref:System.Windows.Media.DrawingBrush> est défini comme le <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> propriété de la <xref:System.Windows.Media.Media3D.DiffuseMaterial> appliqué à un [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] plan.  
  
 **Remarque :** il est souvent souhaitable de définir des valeurs telles que le dessin ci-dessous et les objets complexes en tant que ressources qui peuvent être réutilisées et de simplifieront votre code. Consultez [ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md) pour plus d’informations.  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a>Exemple  
 Le code suivant montre l’exemple complet.  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a>Voir aussi  
 [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Créer une scène 3D](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [Vue d’ensemble des objets de dessin](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Vue d’ensemble des graphiques 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
