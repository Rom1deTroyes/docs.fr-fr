---
title: Étiquettes XML recommandées pour les commentaires de documentation (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: 3b2dec4224006d35fb9add11e170b9dcbeeafcf3
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45649963"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>Étiquettes XML recommandées pour les commentaires de documentation (Visual Basic)
Le compilateur Visual Basic peut traiter les commentaires de documentation dans votre code dans un fichier XML. Vous pouvez utiliser des outils supplémentaires pour traiter le fichier XML dans la documentation.  
  
 Les commentaires XML sont autorisés sur les constructions de code telles que les types et membres de type. Pour les types partiels, qu’une partie du type peut avoir des commentaires XML, bien qu’il n’existe aucune restriction sur le commentaire de ses membres.  
  
> [!NOTE]
>  Commentaires de documentation ne peut pas être appliqués aux espaces de noms. La raison est qu’un espace de noms peut s’étendre sur plusieurs assemblys, et pas tous les assemblys doivent être chargés en même temps.  
  
 Le compilateur traite toute balise XML valid. Les balises suivantes fournissent des fonctionnalités couramment utilisées dans la documentation utilisateur.  
  
||||  
|---|---|---|  
|[\<c>](../../../visual-basic/language-reference/xmldoc/c.md)|[\<code>](../../../visual-basic/language-reference/xmldoc/code.md)|[\<example>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<exception >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<Inclure >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<list>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para>](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<autorisation >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<consultez >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<value>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup> le compilateur vérifie la syntaxe.)  
  
> [!NOTE]
>  Si vous souhaitez des crochets pointus apparaissent dans le texte d’un commentaire de documentation, utilisez `&lt;` et `&gt;`. Par exemple, la chaîne `"&lt;text in angle brackets&gt;"` apparaît sous la forme `<text in angle brackets>`.  
  
## <a name="see-also"></a>Voir aussi  
 [Documentation de votre code avec le langage XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [Guide pratique : créer une documentation XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
