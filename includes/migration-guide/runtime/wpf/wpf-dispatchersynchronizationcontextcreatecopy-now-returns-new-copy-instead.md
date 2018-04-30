### <a name="wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a><span data-ttu-id="74487-101">Le DispatcherSynchronizationContext.CreateCopy WPF retourne désormais une nouvelle copie au lieu de l’instance actuelle</span><span class="sxs-lookup"><span data-stu-id="74487-101">WPF DispatcherSynchronizationContext.CreateCopy now returns a new copy instead of the current instance</span></span>

|   |   |
|---|---|
|<span data-ttu-id="74487-102">Détails</span><span class="sxs-lookup"><span data-stu-id="74487-102">Details</span></span>|<span data-ttu-id="74487-103">Dans .NET Framework 4, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> retournait une référence à l’instance actuelle, principalement pour optimiser les performances.</span><span class="sxs-lookup"><span data-stu-id="74487-103">In the .NET Framework 4, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> returned a reference to the current instance, primarily as a performance optimization.</span></span> <span data-ttu-id="74487-104">Dans le .NET Framework 4.5, il retourne une nouvelle instance, ce qui permet, pour la première fois, de conclure que les références égales indiquent que le thread en cours d’exécution se trouve dans le bon contexte de synchronisation.</span><span class="sxs-lookup"><span data-stu-id="74487-104">In the .NET Framework 4.5, it returns a new instance which makes it possible for the first time to conclude that equal references indicate the executing thread is in the correct synchronization context.</span></span>  <span data-ttu-id="74487-105">Il est peu probable que le code qui vérifie l’identité de ces références soit affecté. Cependant, en raison de cette modification, le code qui appelle <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> doit être testé dans le cadre de la migration vers .NET Framework 4.5 ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="74487-105">It is unlikely that code that checks the identity of these references will be affected, but because of the change, code that calls <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> should be tested as part of migration to the .NET Framework 4.5 or newer.</span></span>|
|<span data-ttu-id="74487-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="74487-106">Suggestion</span></span>|<span data-ttu-id="74487-107">N’oubliez pas que <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> retourne désormais un nouvel objet <xref:System.Threading.SynchronizationContext?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="74487-107">Be aware that <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> will now return a new <xref:System.Threading.SynchronizationContext?displayProperty=name> object.</span></span> <span data-ttu-id="74487-108">Avant, le code qui utilisait l’équivalence des références générées de cette manière ne vérifiait pas réellement si le contexte était approprié. À présent, avec le .NET 4.5 et ultérieur, le contexte est bien vérifié.</span><span class="sxs-lookup"><span data-stu-id="74487-108">Previously, code that used equivalence of references generated this way was not actually checking whether it was in the proper context, but does when built against .NET 4.5 or newer.</span></span>  <span data-ttu-id="74487-109">Bien que cela soit peu susceptible de provoquer des problèmes, l’utilisation des chemins de code concernés doit suffire à déterminer si cela peut poser un problème.</span><span class="sxs-lookup"><span data-stu-id="74487-109">While unlikely to cause issues, exercising the affected code paths should be enough to determine if this poses any problem.</span></span>|
|<span data-ttu-id="74487-110">Portée</span><span class="sxs-lookup"><span data-stu-id="74487-110">Scope</span></span>|<span data-ttu-id="74487-111">Mineur</span><span class="sxs-lookup"><span data-stu-id="74487-111">Minor</span></span>|
|<span data-ttu-id="74487-112">Version</span><span class="sxs-lookup"><span data-stu-id="74487-112">Version</span></span>|<span data-ttu-id="74487-113">4.5</span><span class="sxs-lookup"><span data-stu-id="74487-113">4.5</span></span>|
|<span data-ttu-id="74487-114">Type</span><span class="sxs-lookup"><span data-stu-id="74487-114">Type</span></span>|<span data-ttu-id="74487-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="74487-115">Runtime</span></span>|
|<span data-ttu-id="74487-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="74487-116">Affected APIs</span></span>|<ul><li><xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=nameWithType></li></ul>|
