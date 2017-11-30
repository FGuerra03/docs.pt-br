---
title: "Método IMetaDataAssemblyEmit::DefineExportedType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineExportedType
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 245a485289335b096ee60a8eb3696a087e6871e9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>Método IMetaDataAssemblyEmit::DefineExportedType
Cria um `ExportedType` estrutura que contém os metadados de tipo exportado de especificado e retorna o token de metadados associados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `szName`  
 [in] O nome do tipo a ser exportado. Para a versão 1.1 do common language runtime, o nome do tipo exportado deve corresponder exatamente ao nome fornecido no `TypeDef` para o tipo.  
  
 `tkImplementation`  
 [in] Um token especificando onde o tipo exportado é implementado. Os valores válidos e seus significados associados são:  
  
-   `mdFile`O tipo é implementado em um arquivo diferente dentro desse assembly.  
  
-   `mdAssemblyRef`O tipo é implementado em um assembly diferente.  
  
-   `mdExportedTYpe`O tipo é aninhado dentro de outro tipo.  
  
-   `mdFileNil`O tipo está no mesmo arquivo de manifesto e não é um tipo aninhado.  
  
 `tkTypeDef`  
 [in] Um token de metadados que especifica o tipo a ser exportado. Esse valor é inserido no `TypeDef` tabela no arquivo que implementa o tipo e é relevante somente se esse arquivo está nesse assembly.  
  
 `dwExportedTypeFlags`  
 [in] Uma combinação bit a bit de [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) valores de enumeração que define as configurações de propriedade para o tipo exportado.  
  
 `pmdct`  
 [out] Um ponteiro para o token de metadados retornados que indica o tipo exportado.  
  
## <a name="remarks"></a>Comentários  
 Um `ExportedType` estrutura de metadados deve ser definida para cada tipo que é exposto por este assembly e é implementado em um módulo diferente daquele que contém o manifesto.  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)