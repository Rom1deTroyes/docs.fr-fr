---
title: -keycontainer (Options du compilateur C#)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: 57d3acb4fe128e07020bfe7c85ed86563b16f40a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518401"
---
# <a name="-keycontainer-c-compiler-options"></a>-keycontainer (Options du compilateur C#)
Spécifie le nom du conteneur de la clé de chiffrement.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a>Arguments  
 `string`  
 Nom du conteneur de clé de nom fort.  
  
## <a name="remarks"></a>Notes  
 Quand l’option **-keycontainer** est utilisée, le compilateur crée un composant pouvant être partagé. Le compilateur insère une clé publique à partir du conteneur spécifié dans le manifeste d’assembly et signe l’assembly final avec la clé privée. Pour générer un fichier de clé, tapez `sn -k file` à la ligne de commande. `sn -i` installe la paire de clés dans un conteneur. Cette option n’est pas prise en charge quand le compilateur s’exécute sur CoreCLR. Pour signer un assembly en cas de génération sur CoreCLR, utilisez l’option [-keyfile](keyfile-compiler-option.md).
  
 Si vous compilez avec [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), le nom du fichier de clé est conservé dans le module et incorporé dans l’assembly quand vous compilez ce module dans un assembly avec [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Vous pouvez également spécifier cette option comme attribut personnalisé (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) dans le code source de n'importe quel module MSIL (Microsoft Intermediate Language).  
  
 Vous pouvez également passer vos informations de chiffrement au compilateur avec [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md). Utilisez [-delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) si vous voulez ajouter la clé publique au manifeste d’assembly, mais que vous voulez différer la signature de l’assembly tant qu’il n’a pas été testé.  
  
 Pour plus d’informations, consultez [Création et utilisation d’assemblys avec nom fort](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) et [Différer la signature d’un assembly](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Cette option de compilateur n’est pas disponible dans l'environnement de développement Visual Studio.  
  
 Vous pouvez accéder par programmation à cette option de compilateur avec <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.  
  
## <a name="see-also"></a>Voir aussi

- [Option -keyfile du compilateur C#](keyfile-compiler-option.md)
- [Options du compilateur C#](index.md)  
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
