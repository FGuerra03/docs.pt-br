---
title: "Criação de perfil do tempo de execução"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance counters
- common language runtime, profiling
- Perfmon.exe
- System Monitor
- profiling
- runtime, profiling
- profiling applications
- Performance Console
ms.assetid: ccd68284-f3a8-47b8-bc3f-92e5fe3a1640
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a8f3af4878e0f6911fcc55ec76b26649d517b3b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="runtime-profiling"></a>Criação de perfil do tempo de execução
Criação de perfil é um método de coleta de dados de desempenho em qualquer cenário de desenvolvimento ou de implantação. Esta seção é para desenvolvedores e administradores de sistema que desejam coletar informações sobre o desempenho do aplicativo.  
  
## <a name="tracking-performance-using-the-performance-monitor-perfmonexe"></a>Acompanhamento de desempenho usando o Monitor de Desempenho (Perfmon.exe)  
 O Monitor de Desempenho é a ferramenta mais fácil de usar para criar o perfil de seu aplicativo [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. O Monitor de Desempenho representa graficamente os dados encontrados nos contadores de desempenho do .NET Framework que são instalados com o Common Language Runtime e o [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]. Esses contadores podem ser usados para monitorar tudo, desde o gerenciamento de memória até o desempenho de compilador JIT (Just-In-Time). Eles informam sobre os recursos que seu aplicativo usa, o que é uma medida indireta do desempenho desse aplicativo. Use esses contadores para entender como o aplicativo funciona internamente.  
  
#### <a name="to-run-perfmonexe-on-windows-vista-and-later-versions"></a>Para executar Perfmon.exe no Windows Vista e versões posteriores  
  
1.  No prompt de comando, digite **perfmon**. O console **Monitor de Desempenho** é exibido.  
  
2.  Na pasta **Ferramentas de Monitoramento**, clique em **Monitor de Desempenho**.  
  
3.  Na barra de ferramentas do Monitor de Desempenho, clique no ícone **Adicionar** (sinal de adição) se ele estiver presente. Se não estiver presente, clique com o botão direito do mouse na janela do monitor e selecione a opção **Adicionar Contadores**.  
  
     Isso abre a caixa de diálogo **Adicionar Contadores**. A caixa de listagem **Contadores disponíveis** exibe os objetos de desempenho disponíveis. Há um número de objetos predefinidos para aplicativos do .NET Framework, incluindo aqueles para gerenciamento de memória (**Memória do .NET CLR**), interoperabilidade (**Interoperabilidade do .NET CLR**), tratamento de exceção (**Exceções do .NET CLR**) e multithreading (**.NET CLR LocksAndThreads**). Cada objeto de desempenho inclui uma série de contadores de desempenho individuais. Para obter uma lista de contadores de desempenho disponíveis no Monitor de Desempenho, consulte [Contadores de desempenho](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
4.  Selecione a caixa de seleção ao lado do nome de um objeto de desempenho para exibir a lista de contadores de desempenho individuais aos quais ele dá suporte.  
  
5.  Clique no contador de desempenho que você deseja exibir.  
  
6.  Na caixa de listagem **Instâncias do objeto selecionado**, clique em **\<Todas as instâncias>** para especificar que você deseja monitorar o contador de desempenho para o Common Language Runtime globalmente (ou seja, em todo o sistema).  
  
     -ou-  
  
     Na caixa de listagem **Instâncias do objeto selecionado**, clique em um nome do aplicativo para monitorar o contador de desempenho para esse aplicativo.  
  
     Para diferenciar as várias versões do tempo de execução ou para desfazer a ambiguidade entre vários aplicativos com o mesmo nome, você também deve modificar uma chave do Registro. Para obter mais informações, consulte [Contadores de desempenho e aplicativos lado a lado em processo](../../../docs/framework/debug-trace-profile/performance-counters-and-in-process-side-by-side-applications.md).  
  
> [!NOTE]
>  Quando novos contadores de desempenho são instalados enquanto o console de desempenho está em execução, pare e reinicie o console de desempenho para tornar os novos contadores visíveis.  
  
 Se você deseja criar o perfil de um assembly que existe em uma zona ou em um compartilhamento remoto, verifique se o assembly remoto tem confiança total no computador que executa os contadores de desempenho. Se o assembly não tiverem confiança suficiente, os contadores de desempenho não funcionarão. Para obter informações sobre como conceder confiança em zonas diferentes, consulte [Caspol.exe (ferramenta de política de segurança de acesso do código)](../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md).  
  
> [!NOTE]
>  Em sistemas em que o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] é instalado, o Monitor de Desempenho poderá não exibir os dados dos contadores de desempenho em algumas categorias, tais como **Dados do .NET CLR** e **Rede do .NET CLR**, para aplicativos que foram desenvolvidos usando o [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)]. Se esse for o caso, você pode configurar o Monitor de Desempenho para exibir esses dados, adicionando o elemento [\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) ao arquivo de configuração do aplicativo.  
  
## <a name="reading-and-creating-performance-counters-programmatically"></a>Ler e criar contadores de desempenho de forma programática  
 O [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] fornece classes que você pode usar para acessar de forma programática as mesmas informações de desempenho que estão disponíveis no console de desempenho. Você também pode usar essas classes para criar contadores de desempenho personalizados. A tabela a seguir descreve algumas das classes de monitoramento de desempenho que são fornecidas no [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
|Classe|Descrição|  
|-----------|-----------------|  
|<xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType>|Representa um componente do contador de desempenho do Windows NT. Use essa classe para ler contadores existentes predefinidos ou personalizados e publicar dados de desempenho (gravação) em contadores personalizados.|  
|<xref:System.Diagnostics.PerformanceCounterCategory?displayProperty=nameWithType>|Fornece vários métodos para interagir com os contadores e categorias de contadores no computador.|  
|<xref:System.Diagnostics.PerformanceCounterInstaller?displayProperty=nameWithType>|Especifica um instalador para o componente `PerformanceCounter`.|  
|<xref:System.Diagnostics.PerformanceCounterType?displayProperty=nameWithType>|Especifica a fórmula para calcular o método `NextValue` para uma `PerformanceCounter`.|  
  
## <a name="see-also"></a>Consulte também  
 [Contadores de desempenho](../../../docs/framework/debug-trace-profile/performance-counters.md)
