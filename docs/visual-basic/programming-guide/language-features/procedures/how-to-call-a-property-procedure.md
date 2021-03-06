---
title: 'Comment : appeler une procédure de propriété (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: 61d79b9ff99ec144a9c629872abd2a7e7ebda4d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654815"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a>Comment : appeler une procédure de propriété (Visual Basic)
Vous appelez une procédure de propriété en stockant une valeur dans la propriété ou de récupérer sa valeur. Vous accédez à une propriété la même façon que vous accédez à une variable.  
  
 La propriété `Set` stocke une valeur et son `Get` procédure récupère la valeur. Toutefois, vous n’appelez pas explicitement ces procédures par nom. Vous utilisez la propriété dans une instruction d’assignation ou une expression, tout comme vous permet de stocker ou récupérer la valeur d’une variable. Visual Basic effectue les appels aux procédures de la propriété.  
  
### <a name="to-call-a-propertys-get-procedure"></a>Pour appeler la procédure d’obtention d’une propriété  
  
1.  Utilisez le nom de propriété dans une expression de la même façon que vous utiliseriez un nom de variable. Vous pouvez utiliser une propriété partout où vous pouvez utiliser une variable ou une constante.  
  
     - ou -  
  
     Utilisez le nom de propriété suivant égaux (`=`) connectez-vous à une instruction d’assignation.  
  
     L’exemple suivant lit la valeur de la <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> propriété implicitement en appelant son `Get` procédure.  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]  
  
2.  Si la propriété accepte des arguments, faites suivre le nom de propriété avec des parenthèses pour encadrer la liste d’arguments. S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.  
  
3.  Placez les arguments dans la liste d’arguments entre parenthèses, séparées par des virgules. Assurez-vous de que fournir les arguments dans le même ordre que la propriété définit les paramètres correspondants.  
  
 La valeur de la propriété participe à l’expression comme une variable ou constante serait, ou il est stocké dans la variable ou propriété sur le côté gauche de l’instruction d’assignation.  
  
### <a name="to-call-a-propertys-set-procedure"></a>Pour appeler une propriété Set de la procédure  
  
1.  Utilisez le nom de propriété sur le côté gauche d’une instruction d’assignation.  
  
     L’exemple suivant définit la valeur de la <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> propriété implicitement en appelant le `Set` procédure.  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]  
  
2.  Si la propriété accepte des arguments, faites suivre le nom de propriété avec des parenthèses pour encadrer la liste d’arguments. S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.  
  
3.  Placez les arguments dans la liste d’arguments entre parenthèses, séparées par des virgules. Assurez-vous de que fournir les arguments dans le même ordre que la propriété définit les paramètres correspondants.  
  
 La valeur générée sur le côté droit de l’instruction d’assignation est stockée dans la propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures de propriété](./property-procedures.md)  
 [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)  
 [Property (instruction)](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Différences entre les propriétés et les Variables en Visual Basic](./differences-between-properties-and-variables.md)  
 [Guide pratique : créer une propriété](./how-to-create-a-property.md)  
 [Guide pratique : déclarer une propriété avec des niveaux d’accès mixtes](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Comment : déclarer et appeler une propriété par défaut en Visual Basic](./how-to-declare-and-call-a-default-property.md)  
 [Guide pratique : placer une valeur dans une propriété](./how-to-put-a-value-in-a-property.md)  
 [Guide pratique : obtenir une valeur d’une propriété](./how-to-get-a-value-from-a-property.md)  
 [Get (instruction)](../../../../visual-basic/language-reference/statements/get-statement.md)  
 [Set (instruction)](../../../../visual-basic/language-reference/statements/set-statement.md)
