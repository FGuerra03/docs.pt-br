---
title: Interface1 ICorDebugEval2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2
helpviewer_keywords: ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fbcf36ff7aca84299c55083b4ae135ce0a9ec4f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugeval2-interface1"></a>Interface1 ICorDebugEval2
Estende "ICorDebugEval" para oferecer suporte para tipos genéricos.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|Configura uma chamada para o especificado "ICorDebugFunction", que pode ser aninhada dentro de um tipo cujo construtor usa parâmetros de tipo ou em si pode usar parâmetros de tipos.|  
|[Método CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|Obtém um ponteiro para um novo "ICorDebugValue" do tipo especificado, com um valor inicial de nulo ou zero.|  
|[Método NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|Aloca uma nova matriz do tipo de elemento especificado e dimensões.|  
|[Método NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|Cria um novo objeto de tipo parametrizado e chama o método de construtor do objeto.|  
|[Método NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|Cria um novo objeto de tipo parametrizado da classe especificada sem tentar chamar um método de construtor|  
|[Método NewStringWithLength](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|Cria uma nova cadeia de caracteres de comprimento especificado com o conteúdo especificado.|  
|[Método RudeAbort](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|Anula o cálculo que este `ICorDebugEval2` está executando no momento.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)