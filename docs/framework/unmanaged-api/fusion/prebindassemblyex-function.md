---
title: "Função PreBindAssemblyEx"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- PreBindAssemblyEx
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- PreBindAssemblyEx
helpviewer_keywords:
- PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 05977db8e01d00af6e160cb2993867cf83eb24c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="prebindassemblyex-function"></a>Função PreBindAssemblyEx
Obtém o nome de exibição de pós-política para um assembly.  
  
 Essa função dá suporte à infraestrutura .NET Framework e não se destina a ser usado diretamente no seu código.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pAppCtx`  
 [in] Identifica o contexto do aplicativo.  
  
 `pName`  
 [in] Identifica o nome do assembly.  
  
 `pAsmParent`  
 [in] Identifica o assembly pai. Este parâmetro é ignorado.  
  
 `pwzRuntimeVersion`  
 [in] Identifica a versão de tempo de execução.  
  
 `ppNamePostPolicy`  
 [out] Contém o nome de exibição de pós política de.  
  
 `pvReserved`  
 [in] Reservado para extensibilidade futura. `pvReserved`deve ser uma referência nula.  
  
## <a name="remarks"></a>Comentários  
 O `ppNamePostPolicy` parâmetro de saída é definido somente se a função retorna um HRESULT FUSION_E_REF_DEF_MISMATCH. Caso contrário, será nulo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Funções estáticas globais de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
