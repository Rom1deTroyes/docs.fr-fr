### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a><span data-ttu-id="fa9cb-101">ADO.NET tente maintenant de reconnecter automatiquement les connexions SQL rompues</span><span class="sxs-lookup"><span data-stu-id="fa9cb-101">ADO.NET now attempts to automatically reconnect broken SQL connections</span></span>

|   |   |
|---|---|
|<span data-ttu-id="fa9cb-102">Détails</span><span class="sxs-lookup"><span data-stu-id="fa9cb-102">Details</span></span>|<span data-ttu-id="fa9cb-103">À compter de .NET Framework 4.5.1, le .NET Framework tente de reconnecter automatiquement les connexions SQL rompues.</span><span class="sxs-lookup"><span data-stu-id="fa9cb-103">Beginning in the .NET Framework 4.5.1, the .NET Framework will attempt to automatically reconnect broken SQL connections.</span></span> <span data-ttu-id="fa9cb-104">Bien que cette opération améliore généralement la fiabilité des applications, il existe des cas particuliers où une application doit savoir que la connexion a été perdue afin de pouvoir prendre des mesures lors de la reconnexion.</span><span class="sxs-lookup"><span data-stu-id="fa9cb-104">Although this will typically make apps more reliable, there are edge cases in which an app needs to know that the connection was lost so that it can take some action upon reconnection.</span></span>|
|<span data-ttu-id="fa9cb-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="fa9cb-105">Suggestion</span></span>|<span data-ttu-id="fa9cb-106">Si cette fonctionnalité n’est pas souhaitable pour des raisons de compatibilité, elle peut être désactivée en affectant à la propriété <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=name> d’une chaîne de connexion (ou <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=name>) la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="fa9cb-106">If this feature is undesirable due to compatibility concerns, it can be disabled by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=name> property of a connection string (or <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=name>) to 0.</span></span>|
|<span data-ttu-id="fa9cb-107">Portée</span><span class="sxs-lookup"><span data-stu-id="fa9cb-107">Scope</span></span>|<span data-ttu-id="fa9cb-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="fa9cb-108">Edge</span></span>|
|<span data-ttu-id="fa9cb-109">Version</span><span class="sxs-lookup"><span data-stu-id="fa9cb-109">Version</span></span>|<span data-ttu-id="fa9cb-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="fa9cb-110">4.5.1</span></span>|
|<span data-ttu-id="fa9cb-111">Type</span><span class="sxs-lookup"><span data-stu-id="fa9cb-111">Type</span></span>|<span data-ttu-id="fa9cb-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="fa9cb-112">Runtime</span></span>|
|<span data-ttu-id="fa9cb-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="fa9cb-113">Affected APIs</span></span>|<ul><li><xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)?displayProperty=nameWithType></li></ul>|
