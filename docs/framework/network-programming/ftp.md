---
title: FTP
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e5dc6ee0f2c832e3274a1e58808acfdb56ae804c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862976"
---
# <a name="ftp"></a>FTP
Le.NET Framework fournit une prise en charge complète du protocole FTP avec les classes <xref:System.Net.FtpWebRequest> et <xref:System.Net.FtpWebResponse>. Ces classes sont dérivées de <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse>. Dans la plupart des cas, les classes <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse> fournissent tout ce qui est nécessaire pour effectuer la demande mais, si vous avez besoin d’un accès aux fonctionnalités spécifiques à FTP exposées comme propriétés, vous pouvez convertir ces classes en <xref:System.Net.FtpWebRequest> ou <xref:System.Net.FtpWebResponse>.  
  
## <a name="examples"></a>Exemples  
 Pour plus d’informations, consultez les rubriques suivantes : [Guide pratique pour télécharger des fichiers avec FTP](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [Guide pratique pour charger des fichiers avec FTP](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md) et [Guide pratique pour répertorier le contenu d’un répertoire avec FTP](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).  
  
## <a name="ftp-and-proxies"></a>FTP et proxies  
 Si un proxy (spécifié par la propriété <xref:System.Net.FtpWebRequest.Proxy%2A>) est un proxy HTTP, seules les commandes <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory> et <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> sont prises en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [Accès à Internet via un proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [Exemples de programmation réseau](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Exemple de technologie cliente FTP](https://go.microsoft.com/fwlink/?LinkID=179557)  
 [Exemple de technologie de l’explorateur FTP](https://go.microsoft.com/fwlink/?LinkID=179569)  
 [Utilisation de protocoles d’application](../../../docs/framework/network-programming/using-application-protocols.md)
