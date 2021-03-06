---
title: IfElse With Rules
ms.date: 03/30/2017
ms.assetid: c4ad9bb2-9037-413a-8b14-59ed7b927a9e
ms.openlocfilehash: 31906f04149a0ca7659201965ca565c7fa2af305
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500527"
---
# <a name="ifelse-with-rules"></a>IfElse With Rules
Cet exemple illustre l'utilisation d'une condition de règle avec une activité <xref:System.Workflow.Activities.IfElseActivity>.  
  
 L'exemple transmet un paramètre `OrderValue` depuis l'hôte. La valeur du paramètre est utilisée dans une condition de règle sur la première branche de l'activité <xref:System.Workflow.Activities.IfElseActivity>. Si la valeur est inférieure à 10 000, la première branche s’exécute et le <xref:System.Workflow.Activities.CodeActivity> activité dans la première branche imprime **obtenir l’approbation du gestionnaire** à la console. Si la valeur est supérieure à 10 000, le <xref:System.Workflow.Activities.CodeActivity> une activité dans la deuxième branche s’exécute et imprime **obtenir l’approbation du vice-président**.  
  
### <a name="to-build-the-sample"></a>Pour générer l'exemple  
  
1.  Ouvrez la solution dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Générez la solution en appuyant sur Ctrl+Maj+B.  
  
3.  Exécutez la solution sans débogage en appuyant sur Ctrl+F5.  
  
### <a name="to-run-the-sample"></a>Pour exécuter l'exemple  
  
-   Dans la fenêtre Invite de commandes du Kit de développement logiciel (SDK), exécutez le fichier .exe dans le dossier IfElseWithRules\bin\debug (ou le dossier IfElseWithRules\bin pour la version Visual Basic de l'exemple), situé sous le dossier principal de l'exemple.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer :  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant :  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\IfElseWithRules`  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Workflow.Activities.Rules>  
 <xref:System.Workflow.Activities.IfElseActivity>  
 <xref:System.Workflow.Activities.CodeActivity>  
 <xref:System.Workflow.Activities.Rules.RuleDefinitions>
