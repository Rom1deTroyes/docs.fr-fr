---
title: 'Comment : ajouter et supprimer des onglets avec le contrôle TabControl Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tabs [Windows Forms], removing from pages
- TabPage control
- TabControl control [Windows Forms], adding and removing tabs
- tabs [Windows Forms], adding to pages
- tab pages
ms.assetid: 66d4dfca-41e8-44e3-9c80-fb7ac4cb1619
ms.openlocfilehash: 938dbb4ae695f22d6daff417fbf7176800420aae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525602"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol"></a>Comment : ajouter et supprimer des onglets avec le contrôle TabControl Windows Forms
Par défaut, un <xref:System.Windows.Forms.TabControl> contrôle contient deux <xref:System.Windows.Forms.TabPage> contrôles. Vous pouvez accéder à ces onglets via le <xref:System.Windows.Forms.TabControl.TabPages%2A> propriété.  
  
### <a name="to-add-a-tab-programmatically"></a>Pour ajouter un onglet par programmation  
  
-   Utilisez le <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> méthode de la <xref:System.Windows.Forms.TabControl.TabPages%2A> propriété.  
  
    ```vb  
    Dim myTabPage As New TabPage()  
    myTabPage.Text = "TabPage" & (TabControl1.TabPages.Count + 1)  
    TabControl1.TabPages.Add(myTabPage)  
    ```  
  
    ```csharp  
    string title = "TabPage " + (tabControl1.TabCount + 1).ToString();  
    TabPage myTabPage = new TabPage(title);  
    tabControl1.TabPages.Add(myTabPage);  
    ```  
  
    ```cpp  
    String^ title = String::Concat("TabPage ",  
       (tabControl1->TabCount + 1).ToString());  
    TabPage^ myTabPage = gcnew TabPage(title);  
    tabControl1->TabPages->Add(myTabPage);  
    ```  
  
### <a name="to-remove-a-tab-programmatically"></a>Pour supprimer un onglet par programme  
  
-   Pour supprimer les onglets sélectionnés, utilisez la <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> méthode de la <xref:System.Windows.Forms.TabControl.TabPages%2A> propriété.  
  
     - ou -  
  
-   Pour supprimer tous les onglets, utilisez la <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> méthode de la <xref:System.Windows.Forms.TabControl.TabPages%2A> propriété.  
  
    ```vb  
    ' Removes the selected tab:  
    TabControl1.TabPages.Remove(TabControl1.SelectedTab)  
    ' Removes all the tabs:  
    TabControl1.TabPages.Clear()  
    ```  
  
    ```csharp  
    // Removes the selected tab:  
    tabControl1.TabPages.Remove(tabControl1.SelectedTab);  
    // Removes all the tabs:  
    tabControl1.TabPages.Clear();  
    ```  
  
    ```cpp  
    // Removes the selected tab:  
    tabControl1->TabPages->Remove(tabControl1->SelectedTab);  
    // Removes all the tabs:  
    tabControl1->TabPages->Clear();  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du contrôle TabControl](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [Guide pratique pour ajouter un contrôle à une page d'onglet](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [Guide pratique pour désactiver les pages d'onglets](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [Guide pratique pour modifier l'apparence du contrôle TabControl Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
