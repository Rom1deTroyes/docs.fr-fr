---
title: "Comment : analyser des chemins d'accès dans Visual Basic"
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: 7479f368558a8a8a07c1e6ed588bdfef21a0b1de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585942"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a>Comment : analyser des chemins d'accès dans Visual Basic
L’objet <xref:Microsoft.VisualBasic.FileIO.FileSystem> fournit plusieurs méthodes qui facilitent l’analyse des chemins de fichier.  
  
-   La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> combine deux chemins et affiche un chemin combiné au format correct.  
  
-   La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> retourne le chemin absolu du parent du chemin fourni.  
  
-   La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> retourne un objet <xref:System.IO.FileInfo> qui peut être interrogé pour déterminer les propriétés du fichier, telles que son nom et son chemin.  
  
 Ne vous basez pas sur l’extension de nom de fichier pour déterminer le contenu d’un fichier. Par exemple, le fichier Form1.vb peut ne pas être un fichier source Visual Basic.  
  
### <a name="to-determine-a-files-name-and-path"></a>Pour déterminer le nom et le chemin d’un fichier  
  
-   Utilisez les propriétés <xref:System.IO.FileInfo.DirectoryName%2A> et <xref:System.IO.FileInfo.Name%2A> de l’objet <xref:System.IO.FileInfo> pour déterminer le nom et le chemin d’un fichier. Cet exemple détermine le nom et le chemin d’un fichier, puis les affiche.  
  
     [!code-vb[VbVbcnMyFileSystem#54](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_1.vb)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a>Pour combiner le nom et le répertoire d’un fichier en un chemin complet  
  
-   Utilisez la méthode `CombinePath` , en spécifiant le répertoire et le nom du fichier. Cet exemple combine les chaînes `folderPath` et `fileName` créées dans l’exemple précédent, puis affiche le résultat.  
  
     [!code-vb[VbVbcnMyFileSystem#55](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_2.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>  
 <xref:System.IO.FileInfo>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>  
 [Guide pratique pour placer la collection de fichiers dans un répertoire](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
