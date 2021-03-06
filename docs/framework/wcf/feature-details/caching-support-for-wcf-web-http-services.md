---
title: Prise en charge de la mise en cache pour les services HTTP Web WCF
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: 25b564235b5d2b3b26b5d657f3e5f0bd5d594125
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45972986"
---
# <a name="caching-support-for-wcf-web-http-services"></a>Prise en charge de la mise en cache pour les services HTTP Web WCF
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] vous permet d’utiliser le mécanisme de mise en cache déclaratif déjà disponible dans ASP.NET dans vos services HTTP Web WCF. Il vous permet de mettre en cache les réponses provenant de vos opérations de service HTTP Web WCF. Lorsqu'un utilisateur envoie un HTTP GET à votre service qui est configuré pour la mise en cache, ASP.NET renvoie la réponse mise en cache et la méthode de service n'est pas appelée. Lorsque le cache expire, au prochain envoi d'un HTTP GET par un utilisateur, votre méthode de service est appelée et la réponse est encore une fois mise en cache. Pour plus d’informations sur la mise en cache ASP.NET, consultez [vue d’ensemble de la mise en cache ASP.NET](https://go.microsoft.com/fwlink/?LinkId=152534)  
  
## <a name="basic-web-http-service-caching"></a>Mise en cache du service HTTP Web de base  
 Pour activer la mise en cache du service HTTP WEB, vous devez d'abord activer la compatibilité ASP.NET en appliquant au service l'objet <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> et en attribuant à la propriété <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> la valeur <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> ou <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] introduit un nouvel attribut nommé <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> qui vous permet de spécifier un nom de profil de cache. Cet attribut s'applique à une opération de service. L'exemple suivant applique l'objet <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> à un service pour activer la compatibilité ASP.NET et configure l'opération `GetCustomer` pour la mise en cache. Le <!--zz<xref:System.ServiceModel.Activation.AspNetCacheProfileAttribute>--> `System.ServiceModel.Activation.AspNetCacheProfileAttribute` attribut spécifie un profil de cache qui contient les paramètres de cache à utiliser.  
  
```csharp
[ServiceContract] 
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]
public class Service
{
    [WebGet(UriTemplate = "{id}")]
    [AspNetCacheProfile("CacheFor60Seconds")]
    public Customer GetCustomer(string id)
    {
        // ...
    }
}
```  
  
 Vous devez également activer le mode de compatibilité ASP.NET dans le fichier Web.config, comme indiqué dans l'exemple suivant.  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
>  Si le mode de compatibilité ASP.NET n'est pas activé et si l'attribut <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> est utilisé, une exception est levée.  
  
 Le nom du profil de cache spécifié par l'attribut <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifie un profil de cache qui est ajouté à votre fichier de configuration Web.config. Le profil de cache est défini dans un <`outputCacheSetting`> comme illustré dans l’exemple de configuration suivant.  
  
```xml
<!-- ...  -->
<system.web>  
   <caching>  
      <outputCacheSettings>  
         <outputCacheProfiles>  
            <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable"/>  
         </outputCacheProfiles>  
      </outputCacheSettings>  
   </caching>  
   <!-- ... -->  
</system.web>  
```  
  
 Il s'agit du même élément de configuration que celui disponible pour les applications ASP.NET. Pour plus d’informations sur les profils de cache ASP.NET, consultez <xref:System.Web.Configuration.OutputCacheProfile>. Les attributs du profil de cache les plus importants pour les services HTTP Web sont : `cacheDuration` et `varyByParam`. Ces deux attributs sont nécessaires. `cacheDuration` définit la durée (en secondes) pendant laquelle une réponse doit être mise en cache. `varyByParam` vous permet de spécifier un paramètre de chaîne de requête qui est utilisé pour mettre en cache les réponses. Toutes les demandes effectuées avec des valeurs de paramètre de chaîne de requête différentes sont mises en cache de manière distincte. Par exemple, une fois une demande initiale est établie avec http://MyServer/MyHttpService/MyOperation?param=10 toutes les demandes ultérieures effectuées avec le même URI seraient retournées la réponse mise en cache (tant que la durée du cache n’est pas écoulée). Les réponses à une demande similaire, identique mais dont la valeur de paramètre de chaîne de requête est différente, sont mises en cache de manière distincte. Si vous ne souhaitez pas ce comportement de mise en cache distinct, donnez à l'attribut `varyByParam` la valeur « aucun ».  
  
## <a name="sql-cache-dependency"></a>Dépendance de cache SQL  
 Les réponses du service HTTP Web peuvent également être mises en cache avec une dépendance de cache SQL. Si votre service HTTP Web WCF dépend de données stockées dans une base de données SQL, vous pouvez mettre en cache la réponse du service et invalider la réponse mise en cache lorsque les données dans la table de la base de données SQL changent. Ce comportement est entièrement configuré dans le fichier Web.config. Vous devez d’abord définir une chaîne de connexion dans le <`connectionStrings`> élément.  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 Vous devez ensuite activer la dépendance de cache SQL dans un <`caching`> élément dans le <`system.web`> comme illustré dans l’exemple de configuration suivant.  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>
    </sqlCacheDependency>
    <!-- ... -->
  </caching>
  <!-- ... -->
</system.web>
```  
  
 Dans cet exemple, la dépendance de cache SQL est activée et un temps de sondage de 1000 millisecondes est défini. Chaque fois que le temps de sondage est écoulé, la table de base de données est vérifiée pour détecter les mises à jour. Si des modifications sont détectées, le contenu du cache est supprimé et lors du prochain appel de l'opération de service, une nouvelle réponse est mise en cache. Dans le <`sqlCacheDependency`> élément Ajouter les bases de données et référencer les chaînes de connexion dans le <`databases`> comme illustré dans l’exemple suivant.  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>  
    </sqlCacheDependency>  
    <!-- ... -->  
  </caching>  
  <!-- ... -->  
</system.web>  
```  
  
 Vous devez ensuite configurer les paramètres de cache de sortie dans le <`caching`> comme illustré dans l’exemple suivant.  
  
```xml
<system.web>
  <caching>  
    <!-- ...  -->
    <outputCacheSettings>
      <outputCacheProfiles>
        <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable" />
      </outputCacheProfiles>
    </outputCacheSettings>
  </caching>
  <!-- ... -->
</system.web>
```  
  
 Ici, la durée de mise en cache est définie à 60 secondes, `varyByParam` est défini sur aucun et `sqlDependency` est défini sur une liste délimitée par des points-virgules de paires de nom de base de données/table séparés par le signe deux-points. Lorsque les données dans `MyTable` sont modifiées, la réponse mise en cache pour l'opération de service est supprimée, et lorsque l'opération est appelée, une nouvelle réponse est générée (en appelant l'opération de service), mise en cache et retournée au client.  
  
> [!IMPORTANT]
>  Pour ASP.NET accéder à une base de données SQL, vous devez utiliser le [ASP.NET SQL Server Registration Tool](https://go.microsoft.com/fwlink/?LinkId=152536). De plus, vous devez autoriser le compte d'utilisateur approprié à accéder à la base de données et à la table. Pour plus d’informations, consultez [l’accès à SQL Server à partir d’une Application Web](https://go.microsoft.com/fwlink/?LinkId=178988).  
  
## <a name="conditional-http-get-based-caching"></a>Mise en cache basée sur HTTP GET conditionnel  
 Dans les scénarios HTTP Web un HTTP GET conditionnel est souvent utilisé par les services pour implémenter la mise en cache intelligente des HTTP comme décrit dans la [spécification HTTP](https://go.microsoft.com/fwlink/?LinkId=165800). Pour ce faire, le service doit définir la valeur de l'en-tête ETag dans la réponse HTTP. Il doit également activer l'en-tête If-None-Match dans la requête HTTP pour vérifier si l'un des ETag spécifiés correspond à l'ETag actuel.  
  
 Pour les demandes GET et HEAD, la méthode <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> prend une valeur ETag et la compare à l'en-tête If-None-Match de la demande. Si l'en-tête est présent et qu'il correspond, une exception <xref:System.ServiceModel.Web.WebFaultException> avec un code d'état HTTP 304 (non modifié) est levée et un en-tête ETag est ajouté à la réponse avec l'ETag correspondant.  
  
 Une surcharge de la méthode <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> prend une date de dernière modification et la compare à l'en-tête If-Modified-Since de la demande. Si l'en-tête est présent et que la ressource n'a pas été modifiée depuis, une exception <xref:System.ServiceModel.Web.WebFaultException> avec un code d'état HTTP 304 (non modifié) est levée.  
  
 Pour les demandes PUT, POST et DELETE, la méthode <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> prend la valeur ETag actuelle d'une ressource. Si la valeur ETag actuelle est null, la méthode vérifie que l’en-tête If-None-Match a la valeur « * ».  Si la valeur ETag actuelle n'est pas une valeur par défaut, la méthode vérifie la valeur ETag actuelle par rapport à l'en-tête If- Match de la demande. Dans l'un et l'autre cas, la méthode lève une exception <xref:System.ServiceModel.Web.WebFaultException> avec un code d'état HTTP 412 (Échec de la condition préalable), si l'en-tête attendu n'est pas présent dans la demande ou si sa valeur ne remplit pas la condition de la vérification, et elle attribue la valeur ETag actuelle à l'en-tête ETag de la réponse.  
  
 Les deux méthodes `CheckConditional` et <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> vérifient que la valeur ETag figurant dans l'en-tête de réponse est valide conformément à la spécification HTTP. Cela implique d'entourer la valeur ETag de guillemets doubles, s'il n'y en a pas déjà, et d'éviter soigneusement les caractères de guillemets doubles internes à la valeur. La comparaison de valeurs d'ETag faibles n'est pas prise en charge.  
  
 L'exemple suivant montre l'utilisation de ces méthodes.  
  
```csharp
[WebGet(UriTemplate = "{id}"), Description("Returns the specified customer from customers collection. Returns NotFound if there is no such customer. Supports conditional GET.")]
public Customer GetCustomer(string id)
{
    lock (writeLock)
    {
        // return NotFound if there is no item with the specified id.
        object itemEtag = customerEtags[id];
        if (itemEtag == null)
        {
            throw new WebFaultException(HttpStatusCode.NotFound);
        }
  
        // return NotModified if the client did a conditional GET and the customer item has not changed
        // since when the client last retrieved it
        WebOperationContext.Current.IncomingRequest.CheckConditionalRetrieve((long)itemEtag);
        Customer result = this.customers[id] as Customer;
        
        // set the customer etag before returning the result
        WebOperationContext.Current.OutgoingResponse.SetETag((long)itemEtag);
        return result;
    }
}
```  
  
## <a name="security-considerations"></a>Considérations relatives à la sécurité  
 Les réponses aux demandes qui requièrent une autorisation ne doivent pas être mises en cache, car l'autorisation n'est pas effectuée lorsque la réponse est traitée à partir du cache.  La mise en cache de telles réponses introduirait une faille de sécurité grave.  En règle générale, les demandes qui requièrent une autorisation fournissent des données spécifiques à l'utilisateur, de sorte que la mise en cache côté serveur ne présente aucun avantage.  Dans des situations de ce genre, il est plus approprié d'effectuer une mise en cache côté client, voire aucune mise en cache.
