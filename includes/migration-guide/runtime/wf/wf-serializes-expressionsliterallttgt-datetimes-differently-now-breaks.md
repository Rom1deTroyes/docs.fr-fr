### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a><span data-ttu-id="640da-101">WF sérialise désormais différemment les objets DateTimes Expressions.Literal&lt;T&gt; (il arrête les analyseurs XAML personnalisés)</span><span class="sxs-lookup"><span data-stu-id="640da-101">WF serializes Expressions.Literal&lt;T&gt; DateTimes differently now (breaks custom XAML parsers)</span></span>

|   |   |
|---|---|
|<span data-ttu-id="640da-102">Détails</span><span class="sxs-lookup"><span data-stu-id="640da-102">Details</span></span>|<span data-ttu-id="640da-103">L’objet <xref:System.Windows.Markup.ValueSerializer> associé convertira un objet <xref:System.DateTime?displayProperty=name> ou <xref:System.DateTimeOffset?displayProperty=name> dont les composants Second et <xref:System.DateTime.Millisecond?displayProperty=name> ne sont pas nuls et (pour une valeur de <xref:System.DateTime?displayProperty=name>) dont la propriété <xref:System.DateTime.Kind> n’est pas Unspecified pour la syntaxe d’élément de propriété au lieu d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="640da-103">The associated <xref:System.Windows.Markup.ValueSerializer> object will convert a <xref:System.DateTime?displayProperty=name> or <xref:System.DateTimeOffset?displayProperty=name> object whose Second and <xref:System.DateTime.Millisecond?displayProperty=name> components are non-zero and (for a <xref:System.DateTime?displayProperty=name> value) whose <xref:System.DateTime.Kind> property is not Unspecified to property element syntax instead of a string.</span></span> <span data-ttu-id="640da-104">Cette modification permet aux valeurs <xref:System.DateTime?displayProperty=name> et <xref:System.DateTimeOffset?displayProperty=name> de faire l'objet d'un aller-retour.</span><span class="sxs-lookup"><span data-stu-id="640da-104">This change allows <xref:System.DateTime?displayProperty=name> and <xref:System.DateTimeOffset?displayProperty=name> values to be round-tripped.</span></span> <span data-ttu-id="640da-105">Les analyseurs XAML personnalisés qui supposent que l'entrée XAML figure dans la syntaxe d'attribut ne fonctionnent pas correctement.</span><span class="sxs-lookup"><span data-stu-id="640da-105">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>|
|<span data-ttu-id="640da-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="640da-106">Suggestion</span></span>|<span data-ttu-id="640da-107">Cette modification permet aux valeurs <xref:System.DateTime?displayProperty=name> et <xref:System.DateTimeOffset?displayProperty=name> de faire l'objet d'un aller-retour.</span><span class="sxs-lookup"><span data-stu-id="640da-107">This change allows <xref:System.DateTime?displayProperty=name> and <xref:System.DateTimeOffset?displayProperty=name> values to be round-tripped.</span></span> <span data-ttu-id="640da-108">Les analyseurs XAML personnalisés qui supposent que l'entrée XAML figure dans la syntaxe d'attribut ne fonctionnent pas correctement.</span><span class="sxs-lookup"><span data-stu-id="640da-108">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>|
|<span data-ttu-id="640da-109">Portée</span><span class="sxs-lookup"><span data-stu-id="640da-109">Scope</span></span>|<span data-ttu-id="640da-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="640da-110">Edge</span></span>|
|<span data-ttu-id="640da-111">Version</span><span class="sxs-lookup"><span data-stu-id="640da-111">Version</span></span>|<span data-ttu-id="640da-112">4.5</span><span class="sxs-lookup"><span data-stu-id="640da-112">4.5</span></span>|
|<span data-ttu-id="640da-113">Type</span><span class="sxs-lookup"><span data-stu-id="640da-113">Type</span></span>|<span data-ttu-id="640da-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="640da-114">Runtime</span></span>|
