---
title: Guide pratique pour remplir une arborescence XML avec un XmlWriter (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
ms.openlocfilehash: cd8f8b5c382c64e142d794951ea289a3ca979f81
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530345"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a>Guide pratique pour remplir une arborescence XML avec un XmlWriter (LINQ to XML) (C#)
L'une des manières de remplir une arborescence XML consiste à utiliser <xref:System.Xml.Linq.XContainer.CreateWriter%2A> pour créer un objet <xref:System.Xml.XmlWriter>, puis à écrire dans l'objet <xref:System.Xml.XmlWriter>. L'arborescence XML est remplie avec tous les nœuds écrits dans l'objet <xref:System.Xml.XmlWriter>.  
  
 Cette méthode est généralement utilisée quand [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est utilisé avec une autre classe censée écrire dans un objet <xref:System.Xml.XmlWriter>, comme <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## <a name="example"></a>Exemple  
 Une utilisation possible de <xref:System.Xml.Linq.XContainer.CreateWriter%2A> est lors de l'appel à une transformation XSLT. Cet exemple crée une arborescence XML, crée un objet <xref:System.Xml.XmlReader> à partir de l'arborescence XML, crée un nouveau document, puis crée un objet <xref:System.Xml.XmlWriter> pour écrire dans le nouveau document. Il appelle ensuite la transformation XSLT, en passant <xref:System.Xml.XmlReader> et <xref:System.Xml.XmlWriter>. Une fois la transformation terminée avec succès, la nouvelle arborescence XML est remplie avec les résultats de la transformation.  
  
```csharp  
string xslMarkup = @"<?xml version='1.0'?>  
<xsl:stylesheet xmlns:xsl='http://www.w3.org/1999/XSL/Transform' version='1.0'>  
    <xsl:template match='/Parent'>  
        <Root>  
            <C1>  
            <xsl:value-of select='Child1'/>  
            </C1>  
            <C2>  
            <xsl:value-of select='Child2'/>  
            </C2>  
        </Root>  
    </xsl:template>  
</xsl:stylesheet>";  
  
XDocument xmlTree = new XDocument(  
    new XElement("Parent",  
        new XElement("Child1", "Child1 data"),  
        new XElement("Child2", "Child2 data")  
    )  
);  
  
XDocument newTree = new XDocument();  
using (XmlWriter writer = newTree.CreateWriter())  
{  
    // Load the style sheet.  
    XslCompiledTransform xslt = new XslCompiledTransform();  
    xslt.Load(XmlReader.Create(new StringReader(xslMarkup)));  
  
    // Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer);  
}  
  
Console.WriteLine(newTree);  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>  
- <xref:System.Xml.XmlWriter>  
- <xref:System.Xml.Xsl.XslCompiledTransform>  
- [Création d’arborescences XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
