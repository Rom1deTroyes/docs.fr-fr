---
title: '#pragma warning (référence C#)'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 89ff8151d55ac58a1b114f7727297704ce26b9a7
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44083650"
---
# <a name="pragma-warning-c-reference"></a>#pragma warning (référence C#)
`#pragma warning` peut activer ou désactiver certains avertissements.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
#### <a name="parameters"></a>Paramètres  
 `warning-list`  
 Liste de numéros d’avertissement séparés par des virgules. Le préfixe « CS » est facultatif.  
  
 Quand aucun numéro d’avertissement n’est spécifié, `disable` désactive tous les avertissements et `restore` active tous les avertissements.  
  
> [!NOTE]
>  Pour trouver les numéros d’avertissement dans Visual Studio, générez votre projet, puis recherchez les numéros d’avertissement dans la fenêtre **Sortie**.  
  
## <a name="example"></a>Exemple  
  
```csharp
// pragma_warning.cs  
using System;  
  
#pragma warning disable 414, CS3021  
[CLSCompliant(false)]  
public class C  
{  
    int i = 1;  
    static void Main()  
    {  
    }  
}  
#pragma warning restore CS3021  
[CLSCompliant(false)]  // CS3021  
public class D  
{  
    int i = 1;  
    public static void F()  
    {  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Référence C#](../../../csharp/language-reference/index.md)  
- [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
- [Directives de préprocesseur C#](../../../csharp/language-reference/preprocessor-directives/index.md)  
- [Erreurs du compilateur C#](../../../csharp/language-reference/compiler-messages/index.md)
