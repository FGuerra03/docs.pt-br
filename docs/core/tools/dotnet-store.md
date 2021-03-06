---
title: Comando dotnet store
description: O comando "dotnet store" armazena os assemblies especificados no repositório de pacotes de tempo de execução.
author: bleroy
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 6baa28256535d6a9d653d9df743cd3cdf45ab910
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-store"></a>dotnet store

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a>Nome

`dotnet store` – Armazena os assemblies especificados no [repositório de pacotes de tempo de execução](../deploying/runtime-store.md).

## <a name="synopsis"></a>Sinopse

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a>Descrição

`dotnet store` armazena os assemblies especificados no [repositório de pacotes de tempo de execução](../deploying/runtime-store.md). Por padrão, os assemblies são otimizados para a estrutura e o tempo de execução de destino. Para obter mais informações, consulte o tópico [repositório de pacotes de tempo de execução](../deploying/runtime-store.md).

## <a name="required-options"></a>Opções obrigatórias

`-f|--framework <FRAMEWORK>`

Especifica a [estrutura de destino](../../standard/frameworks.md).

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

O *arquivo de manifesto do repositório de pacotes* é um arquivo XML que contém a lista de pacotes a serem armazenados. O formato do arquivo de manifesto é compatível com o formato *csproj*. Portanto, um arquivo de projeto *csproj* que referencia os pacotes desejados pode ser usado com a opção `-m|--manifest` para armazenar os assemblies no repositório de pacotes de tempo de execução. Para especificar vários arquivos de manifesto, repita a opção e o caminho para cada arquivo: `--manifest packages1.csproj --manifest packages2.csproj`.

`-r|--runtime <RUNTIME_IDENTIFIER>`

O [identificador do tempo de execução](../rid-catalog.md) a ser usado como destino.

## <a name="optional-options"></a>Opções opcionais

`--framework-version <FRAMEWORK_VERSION>`

Especifica a versão do SDK do .NET Core. Essa opção permite que você selecione uma versão da estrutura específica, além da estrutura especificada pela opção `-f|--framework`.

`-h|--help`

Mostra informações de ajuda.

`-o|--output <OUTPUT_DIRECTORY>`

Especifica o caminho para o repositório de pacotes de tempo de execução. Se não for especificado, o padrão será o subdiretório *repositório* do diretório de instalação do .NET Core do perfil do usuário.

`--skip-optimization`

Ignora a fase de otimização.

`--skip-symbols`

Ignora a geração de símbolos. No momento, só é possível gerar símbolos no Windows e no Linux.

`-v|--verbosity <LEVEL>`

Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

O diretório de trabalho usado pelo comando. Se não for especificado, ele usará o subdiretório *obj* do diretório atual.

## <a name="examples"></a>Exemplos

Armazene os pacotes especificados no arquivo de projeto *packages.csproj* para .NET Core 2.0.0:

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

Armazene os pacotes especificados no *packages.csproj* sem otimização:

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a>Consulte também

[Repositório de pacote de tempo de execução](../deploying/runtime-store.md)   
