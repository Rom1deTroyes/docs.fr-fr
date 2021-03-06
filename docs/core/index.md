---
title: Guide .NET Core
description: .NET Core est une implémentation modulaire à hautes performances de .NET pour la création d’applications Windows, Linux et Mac. Découvrez .NET Core pour démarrer.
author: richlander
ms.author: mairaw
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: cfa7c27871204b808c9d753a970d5abb907a183e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512839"
---
# <a name="net-core-guide"></a>Guide .NET Core

[.NET Core](about.md) est une plateforme de développement généraliste [open source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT) qui est tenue à jour par Microsoft et la communauté .NET sur [GitHub](https://github.com/dotnet/core). Cette multiplateforme prend en charge Windows, macOS et Linux. Elle peut être utilisée dans des scénarios d’appareil, de cloud et d’applications IoT.

Consultez [À propos de .NET Core](about.md) pour en savoir plus sur .NET Core, notamment ses caractéristiques, les langues et frameworks pris en charge et les API clés.

Consultez les [Tutoriels .NET Core](tutorials/index.md) pour apprendre à créer une application .NET Core simple. Il suffit de quelques minutes pour créer votre première application et la rendre opérationnelle. Si vous souhaitez tester .NET Core dans votre navigateur, consultez le démarrage rapide [Nombres en C#](https://docs.microsoft.com/dotnet/csharp/quick-starts/hello-world).

## <a name="download-net-core-21"></a>Télécharger .NET Core 2.1

Téléchargez le [SDK .NET Core 2.1](https://www.microsoft.com/net/download) pour tester .NET Core sur votre ordinateur Windows, macOS ou Linux. Visitez [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) si vous préférez utiliser des conteneurs Docker.

Toutes les versions de .NET Core sont disponibles sur [Téléchargements de .NET Core](https://www.microsoft.com/net/download/archives) si vous recherchez une autre version de .NET Core.

## <a name="net-core-21"></a>.NET Core 2.1

La version la plus récente est [.NET Core 2.1](whats-new/dotnet-core-2-1.md). Les nouvelles fonctionnalités incluent : outils généraux, API haute performance (comme <xref:System.Span%601?displayProperty=nameWithType>), compilation JIT à plusieurs niveaux, améliorations des performances de [génération](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) et du [runtime](https://blogs.msdn.microsoft.com/dotnet/2018/04/18/performance-improvements-in-net-core-2-1/), et prise en charge d’Alpine et d’ARM32.

## <a name="create-your-first-application"></a>Créer votre première application

Après avoir installé le SDK .NET Core, ouvrez une invite de commandes. Tapez les commandes `dotnet` suivantes pour créer et exécuter une application C#.

```console
dotnet new console
dotnet run
```

Vous devez voir la sortie suivante :

```console
Hello World!
```

## <a name="support"></a>Assistance

.NET Core est [pris en charge par Microsoft](https://www.microsoft.com/net/support/policy) sur Windows, macOS et Linux. La sécurité et la qualité sont mises à jour plusieurs fois par an, en général, tous les mois.

Les distributions binaires .NET Core sont générées et testées sur des serveurs managés par Microsoft dans Azure et elles sont prises en charge comme tous les produits Microsoft.

[Red Hat prend en charge .NET Core](http://redhatloves.net/) sur Red Hat Enterprise Linux (RHEL). Red Hat génère .NET Core à partir de la source et le rend disponible dans les [collections logicielles Red Hat](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat et Microsoft collaborent pour s’assurer que .NET Core fonctionne correctement sur RHEL.