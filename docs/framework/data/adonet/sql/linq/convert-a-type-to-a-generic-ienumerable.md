---
title: 'Comment : convertir un type en IEnumerable générique'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: e1d8036dd7ef4e1f59e2af46ac101135c39ef0c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360437"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a>Comment : convertir un type en IEnumerable générique
Utilisez <xref:System.Linq.Enumerable.AsEnumerable%2A> pour retourner l'argument typé comme un `IEnumerable` générique.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (à l'aide du `Query` générique par défaut) tente de convertir la requête en SQL et de l'exécuter sur le serveur. Toutefois, la clause `where` fait référence à une méthode côté client définie par l'utilisateur (`isValidProduct`) qui ne peut pas être convertie en SQL.  
  
 La solution consiste à spécifier l'implémentation <xref:System.Collections.Generic.IEnumerable%601> générique côté client de `where` pour remplacer le <xref:System.Linq.IQueryable%601> générique. Vous pouvez pour cela appeler l'opérateur <xref:System.Linq.Enumerable.AsEnumerable%2A>.  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
