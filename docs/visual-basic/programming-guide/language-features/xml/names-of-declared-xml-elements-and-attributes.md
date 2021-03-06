---
title: Nom des attributs et des éléments XML déclarés (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: 9b586936281bfbf2dcace7cf2892bebf305fc842
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650424"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a>Nom des attributs et des éléments XML déclarés (Visual Basic)
Cette rubrique fournit des instructions de Visual Basic pour nommer les éléments XML et les attributs dans les littéraux XML.  Dans un littéral XML, vous pouvez spécifier un nom local ou un nom qualifié. Un nom qualifié se compose d’un préfixe d’espace de noms XML, un signe deux-points et un nom local. Pour plus d’informations sur les préfixes d’espace de noms XML, consultez [XML élément Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="rules"></a>Règles  
 Un nom local d’un élément ou attribut en Visual Basic doit respecter les règles suivantes.  
  
-   Il peut commencer par un espace de noms. Il doit commencer par un caractère alphabétique ou un trait de soulignement (`_`).  
  
-   Il doit contenir uniquement des caractères alphabétiques, des chiffres décimaux, des traits de soulignement, des points (.) et des traits d’union (-).  
  
-   Il ne doit pas être supérieure à 1 024 caractères.  
  
-   Les deux-points qui figurent dans les noms indiquent la délimitation d’espace de noms. Par conséquent, vous pouvez utiliser des signes deux-points uniquement pour spécifier un espace de noms XML pour un nom particulier.  
  
 En outre, vous devez respecter la règle suivante.  
  
-   La spécification XML 1.0 réserve tous les noms commençant par la chaîne « xml » de toute variation de la mise en majuscules. Par conséquent, n’utilisez pas ces noms pour votre élément et les noms d’attributs.  
  
### <a name="name-length-guidelines"></a>Instructions de longueur de nom  
 Dans la pratique, un nom doit être aussi court que possible tout en identifiant clairement la nature de l’élément. Cela améliore la lisibilité de votre code et réduit la taille du fichier source et de longueur de ligne.  
  
 Toutefois, votre nom ne doit pas être court qu’il ne pas décrive correctement l’élément ou la façon dont votre code utilise. Ceci est important pour la lisibilité de votre code. Si quelqu'un d’autre tente de le comprendre, ou si vous devez l’observer longtemps après que l’avoir écrit, noms d’éléments appropriés peuvent gagner du temps.  
  
## <a name="case-sensitivity-in-names"></a>Respect de la casse dans les noms  
 Noms d’éléments XML respectent la casse. Cela signifie que lorsque le compilateur Visual Basic compare deux noms qui ne diffèrent que par la casse, il les interprète comme des noms différents. Par exemple, il interprète `ABC` et `abc` comme deux éléments distincts.  
  
## <a name="xml-namespaces"></a>Espaces de noms XML  
 Lorsque vous créez un élément XML littéral, vous pouvez spécifier le préfixe d’espace de noms XML pour le nom de l’élément. Pour plus d’informations, consultez [XML élément Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création de code XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Littéral d’élément XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
