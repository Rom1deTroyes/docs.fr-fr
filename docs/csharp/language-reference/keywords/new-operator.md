---
title: new, opérateur (référence C#)
ms.date: 03/15/2018
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 362217b247bd2ab7a2eec2f86cbaaf1a0652a3ad
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46706474"
---
# <a name="new-operator-c-reference"></a>new, opérateur (référence C#)

Cet opérateur s’utilise pour créer des objets et appeler des constructeurs. Exemple :

```csharp
Class1 obj  = new Class1();
```

Il est également utilisé pour créer des instances de types anonymes :

```csharp
var query = from cust in customers
            select new { Name = cust.Name, Address = cust.PrimaryAddress };
```

L’opérateur `new` est aussi utilisé pour appeler le constructeur par défaut pour les types valeur. Exemple :

```csharp
int i = new int();
```

Dans l’instruction précédente, `i` est initialisé à `0`, qui est la valeur par défaut pour le type `int`. L’instruction produit le même résultat que ce qui suit :

```csharp
int i = 0;
```

Pour obtenir une liste complète des valeurs par défaut, consultez [Tableau des valeurs par défaut](default-values-table.md).

N’oubliez pas qu’il est incorrect de déclarer un constructeur par défaut pour un [struct](struct.md), car chaque type valeur a implicitement un constructeur public par défaut. Il est possible de déclarer des constructeurs paramétrables sur un type struct pour définir ses valeurs initiales, mais cela est nécessaire uniquement si d’autres valeurs que la valeur par défaut sont requises.

Les objets de type valeur, tels que les structs, et les objets de type référence, tels que les classes, sont détruits automatiquement, mais les objets de type valeur sont détruits quand leur contexte contenant est détruit alors que les objets de type référence sont détruits par le garbage collector à une heure non spécifiée une fois que la dernière référence à ceux-ci est supprimée. Pour les types qui contiennent des ressources telles que des handles de fichiers ou des connexions réseau, il est préférable d’employer le nettoyage déterministe pour vous assurer que les ressources qu’ils contiennent sont libérées dès que possible. Pour plus d’informations, consultez [using, instruction](using-statement.md).

L’opérateur `new` ne peut pas être surchargé.

Si l’opérateur `new` ne réussit pas à allouer de la mémoire, il lève l’exception <xref:System.OutOfMemoryException>.

## <a name="example"></a>Exemple

Dans l’exemple suivant, un objet `struct` et un objet de classe sont créés et initialisés à l’aide de l’opérateur `new`, puis des valeurs leur sont assignées. La valeur par défaut et les valeurs assignées sont affichées.

[!code-csharp[csrefKeywordsOperator#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#7)]

Notez que, dans l’exemple, la valeur par défaut d’une chaîne est `null`. Elle n’est donc pas affichée.

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Référence C#](../../language-reference/index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](index.md)
- [Mots clés des opérateurs](operator-keywords.md)
- [new](new.md)
- [Types anonymes](../../programming-guide/classes-and-structs/anonymous-types.md)