### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a><span data-ttu-id="7c1f6-101">WebUtility.HtmlDecode ne décode plus les séquences d’entrée non valides</span><span class="sxs-lookup"><span data-stu-id="7c1f6-101">WebUtility.HtmlDecode no longer decodes invalid input sequences</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7c1f6-102">Détails</span><span class="sxs-lookup"><span data-stu-id="7c1f6-102">Details</span></span>|<span data-ttu-id="7c1f6-103">Par défaut, les méthodes de décodage ne décodent plus une séquence d'entrée non valide en une chaîne UTF-16 non valide.</span><span class="sxs-lookup"><span data-stu-id="7c1f6-103">By default, decoding methods no longer decode an invalid input sequence into an invalid UTF-16 string.</span></span> <span data-ttu-id="7c1f6-104">Au lieu de cela, elles retournent l'entrée d'origine.</span><span class="sxs-lookup"><span data-stu-id="7c1f6-104">Instead, they return the original input.</span></span>|
|<span data-ttu-id="7c1f6-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="7c1f6-105">Suggestion</span></span>|<span data-ttu-id="7c1f6-106">Le changement lié à la sortie du décodeur doit importer uniquement si vous stockez des données binaires à la place de données UTF-16 dans les chaînes.</span><span class="sxs-lookup"><span data-stu-id="7c1f6-106">The change in decoder output should matter only if you store binary data instead of UTF-16 data in strings.</span></span> <span data-ttu-id="7c1f6-107">Pour contrôler explicitement ce comportement, affectez à l’attribut <code>aspnet:AllowRelaxedUnicodeDecoding</code> de l’élément [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) la valeur <code>true</code> pour activer le comportement hérité ou la valeur <code>false</code> pour activer le comportement actuel.</span><span class="sxs-lookup"><span data-stu-id="7c1f6-107">To explicitly control this behavior, set the <code>aspnet:AllowRelaxedUnicodeDecoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) element to <code>true</code> to enable legacy behavior or to <code>false</code> to enable the current behavior.</span></span>|
|<span data-ttu-id="7c1f6-108">Portée</span><span class="sxs-lookup"><span data-stu-id="7c1f6-108">Scope</span></span>|<span data-ttu-id="7c1f6-109">Mineur</span><span class="sxs-lookup"><span data-stu-id="7c1f6-109">Minor</span></span>|
|<span data-ttu-id="7c1f6-110">Version</span><span class="sxs-lookup"><span data-stu-id="7c1f6-110">Version</span></span>|<span data-ttu-id="7c1f6-111">4.5</span><span class="sxs-lookup"><span data-stu-id="7c1f6-111">4.5</span></span>|
|<span data-ttu-id="7c1f6-112">Type</span><span class="sxs-lookup"><span data-stu-id="7c1f6-112">Type</span></span>|<span data-ttu-id="7c1f6-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="7c1f6-113">Runtime</span></span>|
|<span data-ttu-id="7c1f6-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="7c1f6-114">Affected APIs</span></span>|<ul><li><xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType></li></ul>|
