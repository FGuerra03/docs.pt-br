---
title: "Método IMetaDataImport::FindField"
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
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3178d3ff3c64de5390e1150445f0c49c560aa32a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportfindfield-method"></a>Método IMetaDataImport::FindField
Obtém um ponteiro para o FieldDef token para o campo que é incluído por especificado <xref:System.Type> e que tem a assinatura de nome e os metadados especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `td`  
 [in] O token de TypeDef para a classe ou interface que inclui o campo a ser pesquisado. Se esse valor for `mdTokenNil`, a pesquisa é feita para uma variável global.  
  
 `szName`  
 [in] O nome do campo a ser pesquisado.  
  
 `pvSigBlob`  
 [in] Um ponteiro para a assinatura de binários de metadados do campo.  
  
 `cbSigBlob`  
 [in] O tamanho em bytes do `pvSigBlob`.  
  
 `pmb`  
 [out] Um ponteiro para o token FieldDef correspondente.  
  
## <a name="remarks"></a>Comentários  
 Especifique o campo usando sua classe ou interface de delimitador (`td`), seu nome (`szName`) e, opcionalmente, sua assinatura (`pvSigBlob`).  
  
 A assinatura é passado para `FindField` deve foram gerados no escopo atual, porque as assinaturas associadas a um determinado escopo. Uma assinatura pode inserir um token que identifica o tipo de valor ou classe delimitador. (O token é um índice na tabela de TypeDef local). Você não pode criar uma assinatura de tempo de execução fora do contexto do escopo atual e usar essa assinatura como entrada para `FindField`.  
  
 `FindField`localiza apenas os campos que foram definidos diretamente na classe ou interface. campos herdados não for encontrada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
