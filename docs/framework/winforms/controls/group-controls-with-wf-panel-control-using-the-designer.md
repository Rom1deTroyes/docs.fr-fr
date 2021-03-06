---
title: "Comment : grouper les contrôles avec le contrôle Panel Windows Forms à l'aide du concepteur"
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: 99bfcd96dea1bb92866127095a422003bf01f7cd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506872"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a>Comment : grouper les contrôles avec le contrôle Panel Windows Forms à l'aide du concepteur
Windows Forms <xref:System.Windows.Forms.Panel> contrôles sont utilisés pour regrouper d’autres contrôles. Il existe trois raisons pour regrouper des contrôles. Regroupement d’éléments connexes pour une interface utilisateur claire ; visuel regroupement de programmation, des cases d’option, par exemple ; la dernière est pour déplacer les contrôles en tant qu’unité au moment du design.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-a-group-of-controls"></a>Pour créer un groupe de contrôles  
  
1.  Faites glisser un <xref:System.Windows.Forms.Panel> contrôle depuis la **Windows Forms** onglet de la boîte à outils sur un formulaire.  
  
2.  Ajoutez des contrôles pour le dessin du panneau, chacun à l’intérieur du panneau.  
  
     Si vous avez des contrôles existants que vous souhaitez placer dans un panneau, vous pouvez sélectionner tous les contrôles, les couper dans le Presse-papiers, sélectionnez le <xref:System.Windows.Forms.Panel> contrôler et collez-les dans le panneau de configuration. Vous pouvez également faites-les glisser dans le panneau de configuration.  
  
3.  (Facultatif) Si vous souhaitez ajouter une bordure à un panneau, définissez son <xref:System.Windows.Forms.BorderStyle> propriété. Il existe trois possibilités : <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, et <xref:System.Windows.Forms.BorderStyle.None>.  
  
## <a name="see-also"></a>Voir aussi  
 [Panel, contrôle](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [Vue d’ensemble du contrôle Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [Guide pratique pour définir l'arrière-plan d'un contrôle Panel](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md)
