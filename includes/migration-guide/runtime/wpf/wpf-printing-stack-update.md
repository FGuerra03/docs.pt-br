### <a name="wpf-printing-stack-update"></a><span data-ttu-id="059a8-101">Atualização da pilha de impressão do WPF</span><span class="sxs-lookup"><span data-stu-id="059a8-101">WPF Printing Stack Update</span></span>

|   |   |
|---|---|
|<span data-ttu-id="059a8-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="059a8-102">Details</span></span>|<span data-ttu-id="059a8-103">Agora, as APIs de Impressão do WPF que usam <xref:System.Printing.PrintQueue?displayProperty=name>chamam a API de Impressão Pacote de Documentos do Windows em vez da API de Impressão XPS, que foi preterida.</span><span class="sxs-lookup"><span data-stu-id="059a8-103">WPF's Printing APIs using <xref:System.Printing.PrintQueue?displayProperty=name> now call Window's Print Document Package API in favor of the now deprecated XPS Print API.</span></span> <span data-ttu-id="059a8-104">A alteração foi feita para fins de manutenção. Nem usuários nem os desenvolvedores devem ver todas as alterações no comportamento ou no uso da API.</span><span class="sxs-lookup"><span data-stu-id="059a8-104">The change was made with serviceability in mind; neither users nor developers should see any changes in behavior or API usage.</span></span> <span data-ttu-id="059a8-105">A nova pilha de impressão é habilitada por padrão ao ser executada na Atualização do Windows 10 para Criadores.</span><span class="sxs-lookup"><span data-stu-id="059a8-105">The new printing stack is enabled by default when running in Windows 10 Creators Update.</span></span> <span data-ttu-id="059a8-106">A pilha de impressão antiga continuará a funcionar como antes nas versões mais antigas do Windows.</span><span class="sxs-lookup"><span data-stu-id="059a8-106">The old printing stack will still continue to work just as before in older Windows versions.</span></span>|
|<span data-ttu-id="059a8-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="059a8-107">Suggestion</span></span>|<span data-ttu-id="059a8-108">Para usar a pilha antiga na Atualização do Windows 10 para Criadores, defina o valor REG_DWORD <code>UseXpsOMPrinting</code> da chave do Registro <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> como <code>1</code>.</span><span class="sxs-lookup"><span data-stu-id="059a8-108">To use the old stack in Windows 10 Creators Update, set the <code>UseXpsOMPrinting</code> REG_DWORD value of the <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> registry key to <code>1</code>.</span></span>|
|<span data-ttu-id="059a8-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="059a8-109">Scope</span></span>|<span data-ttu-id="059a8-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="059a8-110">Edge</span></span>|
|<span data-ttu-id="059a8-111">Versão</span><span class="sxs-lookup"><span data-stu-id="059a8-111">Version</span></span>|<span data-ttu-id="059a8-112">4.7</span><span class="sxs-lookup"><span data-stu-id="059a8-112">4.7</span></span>|
|<span data-ttu-id="059a8-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="059a8-113">Type</span></span>|<span data-ttu-id="059a8-114">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="059a8-114">Runtime</span></span>|
