---
title: facet
ms.date: 03/30/2017
ms.assetid: 91c4e6aa-3e54-4b6c-a38a-abf27808cc85
ms.openlocfilehash: 2b263a107eae7c75b035dcb4675725556e0f9c2b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="facet"></a>facet
Um *faceta* é usado para adicionar detalhes a uma definição de propriedade do tipo primitivo. Um [propriedade](../../../../docs/framework/data/adonet/property.md) definição contém informações sobre o tipo de propriedade, mas geralmente é necessário obter mais detalhes. Por exemplo, um tipo de entidade em um modelo conceitual pode ter uma propriedade do tipo `String` cujo valor pode não ser definido como nulo. As facetas permitem que você especifique esse nível de detalhe.  
  
 A tabela a seguir descreve as facetas que são suportadas em EDM.  
  
> [!NOTE]
>  Os valores precisos e os comportamentos de facetas são determinados pelo ambiente de tempo de execução usando uma implementação de EDM.  
  
|Aspecto|Descrição|Aplica-se a|  
|-----------|-----------------|----------------|  
|`Collation`|Especifica a sequência de agrupamento (ou sequência de classificação) a ser usadas para executar a comparação e em ordenação operações em valores de propriedade.|`String`|  
|`ConcurrencyMode`|Indica que o valor da propriedade deve ser usado para verificação de simultaneidade otimista.|As propriedades do tipo primitivo|  
|`Default`|Especifica o valor de propriedade padrão se nenhum valor é fornecido em cima de instanciação.|As propriedades do tipo primitivo|  
|`FixedLength`|Especifica se o comprimento do valor da propriedade pode variar.|`Binary`, `String`|  
|`MaxLength`|Especifica o comprimento máximo de valor de propriedade.|`Binary`, `String`|  
|`Nullable`|Especifica se a propriedade pode ter um valor nulo.|As propriedades do tipo primitivo|  
|`Precision`|Para propriedades de tipo `Decimal`, especifica o número de dígitos que um valor de propriedade pode ter. Para propriedades de tipo `Time`, `DateTime`, e `DateTimeOffset`, especifique o número de dígitos para a parte fracionária de segundos de valor de propriedade.|`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,|  
|`Scale`|Especifica o número de dígitos à direita do ponto decimal para o valor da propriedade.|Decimal|  
|`Unicode`|Indica se o valor da propriedade é armazenado como Unicode.|`String`|  
  
## <a name="example"></a>Exemplo  
 O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais. CSDL seguir define um tipo de entidade de `Book` . Observe que as facetas são implementadas como atributos XML. Os valores de aspecto indica que nenhuma propriedade pode ser definida para nulo, e que `Scale` e `Precision` de propriedade de cada `Revision` são definidas como 29.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>Consulte também  
 [Principais conceitos do Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model.md)
