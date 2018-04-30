### <a name="wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a><span data-ttu-id="c1747-101">DispatcherSynchronizationContext.CreateCopy do WPF agora retorna uma nova cópia em vez da instância atual</span><span class="sxs-lookup"><span data-stu-id="c1747-101">WPF DispatcherSynchronizationContext.CreateCopy now returns a new copy instead of the current instance</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c1747-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="c1747-102">Details</span></span>|<span data-ttu-id="c1747-103">No .NET Framework 4, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> retornava uma referência à instância atual, basicamente como uma otimização de desempenho.</span><span class="sxs-lookup"><span data-stu-id="c1747-103">In the .NET Framework 4, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> returned a reference to the current instance, primarily as a performance optimization.</span></span> <span data-ttu-id="c1747-104">No .NET Framework 4.5, ele retorna uma nova instância que possibilita, pela primeira vez, concluir que referências iguais indicam que o thread em execução está no contexto de sincronização correto.</span><span class="sxs-lookup"><span data-stu-id="c1747-104">In the .NET Framework 4.5, it returns a new instance which makes it possible for the first time to conclude that equal references indicate the executing thread is in the correct synchronization context.</span></span>  <span data-ttu-id="c1747-105">É provável que o código que verifica a identidade dessas referências seja afetado, mas, por causa da alteração, o código que chama <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> deve ser testado como parte da migração para o .NET Framework 4.5 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="c1747-105">It is unlikely that code that checks the identity of these references will be affected, but because of the change, code that calls <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> should be tested as part of migration to the .NET Framework 4.5 or newer.</span></span>|
|<span data-ttu-id="c1747-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="c1747-106">Suggestion</span></span>|<span data-ttu-id="c1747-107">Lembre-se de que <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> agora retornará um novo objeto <xref:System.Threading.SynchronizationContext?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="c1747-107">Be aware that <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> will now return a new <xref:System.Threading.SynchronizationContext?displayProperty=name> object.</span></span> <span data-ttu-id="c1747-108">Antigamente, o código que usava equivalência de referências gerada dessa maneira não era de fato verificado se estava no contexto apropriado, mas agora o é quando compilado no .NET 4.5 ou mais recente.</span><span class="sxs-lookup"><span data-stu-id="c1747-108">Previously, code that used equivalence of references generated this way was not actually checking whether it was in the proper context, but does when built against .NET 4.5 or newer.</span></span>  <span data-ttu-id="c1747-109">Embora não haja probabilidade de causar problemas, praticar os caminhos de código afetados deve ser suficiente para determinar se isso impõe algum problema.</span><span class="sxs-lookup"><span data-stu-id="c1747-109">While unlikely to cause issues, exercising the affected code paths should be enough to determine if this poses any problem.</span></span>|
|<span data-ttu-id="c1747-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="c1747-110">Scope</span></span>|<span data-ttu-id="c1747-111">Secundário</span><span class="sxs-lookup"><span data-stu-id="c1747-111">Minor</span></span>|
|<span data-ttu-id="c1747-112">Versão</span><span class="sxs-lookup"><span data-stu-id="c1747-112">Version</span></span>|<span data-ttu-id="c1747-113">4.5</span><span class="sxs-lookup"><span data-stu-id="c1747-113">4.5</span></span>|
|<span data-ttu-id="c1747-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="c1747-114">Type</span></span>|<span data-ttu-id="c1747-115">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="c1747-115">Runtime</span></span>|
|<span data-ttu-id="c1747-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="c1747-116">Affected APIs</span></span>|<ul><li><xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=nameWithType></li></ul>|
