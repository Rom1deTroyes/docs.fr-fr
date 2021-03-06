---
title: "Comment : modifier l'apparence du texte et des images de ToolStrip dans les Windows Forms"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], appearance
- toolbars [Windows Forms], images
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], appearance
- ToolStrip control [Windows Forms], images
- ToolStrip control [Windows Forms], text
- toolbars [Windows Forms], text
ms.assetid: d62dc9d1-2edd-4dfa-aed7-1335d6e13d86
ms.openlocfilehash: d3f53291e24d6a57e798725b716a7fd56eb661b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530528"
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a>Comment : modifier l'apparence du texte et des images de ToolStrip dans les Windows Forms
Vous pouvez contrôler si le texte et les images sont affichées sur un <xref:System.Windows.Forms.ToolStripItem> et comment ils sont alignés par rapport à l’autre et <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a>Pour définir ce qui est affiché sur un ToolStripItem  
  
-   Définir le <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> propriété la valeur souhaitée. Les possibilités sont `Image`, `ImageAndText`, `None`, et `Text`. La valeur par défaut est `ImageAndText`.  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a>Pour aligner le texte sur un ToolStripItem  
  
-   Définir le <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> propriété la valeur souhaitée. Les possibilités sont n’importe quelle combinaison de haut, au milieu et en bas à gauche, centre et droite. La valeur par défaut est `MiddleCenter`.  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a>Pour aligner une image sur un ToolStripItem  
  
-   Définir le <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> propriété la valeur souhaitée. Les possibilités sont n’importe quelle combinaison de haut, au milieu et en bas à gauche, centre et droite. La valeur par défaut est `MiddleLeft`.  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a>Pour définir l’affichent des images et du texte de ToolStripItem entre eux  
  
-   Définir le <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> propriété la valeur souhaitée. Les possibilités sont `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, et `TextBeforeImage`. La valeur par défaut est `ImageBeforeText`.  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.ToolStrip>  
 [Vue d’ensemble du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [Architecture du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [Résumé de la technologie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
