---
title: 'Comment : définir le texte affiché par un contrôle Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, captions
- Button control [Windows Forms], button text
- StdFont object and CommandButton caption
- captions [Windows Forms], Windows Forms controls
- Text property [Windows Forms], Windows Forms control
- Button control [Windows Forms], text display
- labels [Windows Forms], adding to CommandButton control
- buttons [Windows Forms], text
- captions [Windows Forms], setting
- text
- examples [Windows Forms], controls
- text [Windows Forms], Windows Forms controls
- controls [Windows Forms], captions
- forms [Windows Forms], captions
ms.assetid: 36b95bff-8780-479d-b86a-f1a0673653aa
ms.openlocfilehash: d9c9bea26cfc3d5b2cfc4484173a7680ff2fc34d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525033"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a>Comment : définir le texte affiché par un contrôle Windows Forms
Généralement, les contrôles Windows Forms affichent du texte en rapport avec la fonction principale du contrôle. Par exemple, un contrôle <xref:System.Windows.Forms.Button> affiche habituellement une légende indiquant l'action à exécuter quand le bouton est activé. Pour tous les contrôles, vous pouvez définir ou retourner le texte à l'aide de la propriété <xref:System.Windows.Forms.Control.Text%2A>. Vous pouvez modifier la police en utilisant la propriété <xref:System.Windows.Forms.Control.Font%2A>. Vous pouvez également définir le texte à l'aide du concepteur.  Consultez également [Comment : créer des accès clés pour Windows Forms contrôles à l’aide du concepteur](how-to-create-access-keys-for-windows-forms-controls-using-the-designer.md), [Comment : définir le texte affiché par un contrôle Windows Forms à l’aide du concepteur](how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer.md), [Comment : définir l’Image Affiché par un Windows Forms à l’aide du Concepteur de contrôle](how-to-set-the-image-displayed-by-a-windows-forms-control-using-the-designer.md).  
  
### <a name="to-set-the-text-displayed-by-a-control-programmatically"></a>Pour définir le texte affiché par un contrôle par programmation  
  
1.  Affectez une chaîne comme valeur de la propriété <xref:System.Windows.Forms.Control.Text%2A>.  
  
     Pour créer une touche d'accès soulignée, incluez une esperluette (&) avant la lettre qui sera la touche d'accès.  
  
2.  Affectez un objet de type <xref:System.Drawing.Font> comme valeur de la propriété <xref:System.Windows.Forms.Control.Font%2A>.  
  
    ```vb  
    Button1.Text = "Click here to save changes"  
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)  
    ```  
  
    ```csharp  
    button1.Text = "Click here to save changes";  
    button1.Font = new Font("Arial", 10, FontStyle.Bold,  
       GraphicsUnit.Point);  
    ```  
  
    ```cpp  
    button1->Text = "Click here to save changes";  
    button1->Font = new System::Drawing::Font("Arial",  
       10, FontStyle::Bold, GraphicsUnit::Point);  
    ```  
  
    > [!NOTE]
    >  Vous pouvez utiliser un caractère d'échappement pour afficher un caractère spécial dans des éléments d'interface utilisateur qui l'interpréteraient normalement différemment, tels que des éléments de menu. Par exemple, la ligne de code suivante définit le texte de l'élément de menu pour qu'il indique « & Now For Something Completely Different » :  
  
    ```vb  
    MPMenuItem.Text = "&& Now For Something Completely Different"  
    ```  
  
    ```csharp  
    mpMenuItem.Text = "&& Now For Something Completely Different";  
    ```  
  
    ```cpp  
    mpMenuItem->Text = "&& Now For Something Completely Different";  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>  
 [Guide pratique pour créer des touches d'accès rapide pour des contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)  
 [Guide pratique pour répondre à un clic du contrôle Button Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)
