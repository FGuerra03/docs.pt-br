---
title: "Método IMetaDataEmit::DefineParam"
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
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f4bf36edfad504f2858a45d5e34891042d8850bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefineparam-method"></a>Método IMetaDataEmit::DefineParam
Cria uma definição de parâmetro com a assinatura especificada para o método referenciada pelo token de especificado e obtém um token para que a definição de parâmetro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DefineParam (  
    [in]  mdMethodDef md,   
    [in]  ULONG       ulParamSeq,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,   
    [out] mdParamDef  *ppd   
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `md`  
 [in] O token para o método cujo parâmetro está sendo definido.  
  
 `ulParamSeq`  
 [in] O número de sequência do parâmetro.  
  
 `szName`  
 [in] O nome do parâmetro em Unicode.  
  
 `dwParamFlags`  
 [in] Sinalizadores para o parâmetro. Esse é um bitmask de `CorParamAttr` valores.  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_`  *\**  para o valor da constante.  
  
 `pValue`  
 [in] O valor da constante para o parâmetro.  
  
 `cchValue`  
 [in] O tamanho, em caracteres Unicode, de `pValue`.  
  
 `ppd`  
 [out] O `mdParamDef` token atribuído.  
  
## <a name="remarks"></a>Comentários  
 Os valores de sequência em `ulParamSeq` começam com 1 para parâmetros. Um valor de retorno tem um número de sequência de 0.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
