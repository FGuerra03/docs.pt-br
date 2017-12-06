---
title: "Tipos de nós XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71d03b78-6898-4ce7-b0fc-1282573f31f7
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3914a2c5c06a2cc73f14bc473984094b474d537e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="types-of-xml-nodes"></a><span data-ttu-id="5daa5-102">Tipos de nós XML</span><span class="sxs-lookup"><span data-stu-id="5daa5-102">Types of XML Nodes</span></span>
<span data-ttu-id="5daa5-103">Quando um documento XML é lido na memória como uma árvore de nós, os tipos de nós são decididos quando os nós são criados.</span><span class="sxs-lookup"><span data-stu-id="5daa5-103">When an XML document is read into memory as a tree of nodes, the node types for the nodes are decided when the nodes are created.</span></span> <span data-ttu-id="5daa5-104">A especificação DOM (Document Object Model) XML tem vários tipos de nós, determinados pelo W3C (World Wide Web Consortium) e listados na seção 1.1.1 (The DOM Structure Model).</span><span class="sxs-lookup"><span data-stu-id="5daa5-104">The XML Document Object Model (DOM) has several kinds of node types, determined by the World Wide Web Consortium (W3C) and listed in section 1.1.1 The DOM Structure Model.</span></span> <span data-ttu-id="5daa5-105">A tabela a seguir lista os tipos de nós, o objeto atribuído ao tipo de nó e uma breve descrição de cada tipo.</span><span class="sxs-lookup"><span data-stu-id="5daa5-105">The following table lists the node types, the object assigned to that node type, and a short description of each.</span></span>  
  
|<span data-ttu-id="5daa5-106">Tipo de nó DOM</span><span class="sxs-lookup"><span data-stu-id="5daa5-106">DOM node type</span></span>|<span data-ttu-id="5daa5-107">Objeto</span><span class="sxs-lookup"><span data-stu-id="5daa5-107">Object</span></span>|<span data-ttu-id="5daa5-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="5daa5-108">Description</span></span>|  
|-------------------|------------|-----------------|  
|<span data-ttu-id="5daa5-109">Documento</span><span class="sxs-lookup"><span data-stu-id="5daa5-109">Document</span></span>|<xref:System.Xml.XmlDocument>|<span data-ttu-id="5daa5-110">O contêiner de todos os nós na árvore.</span><span class="sxs-lookup"><span data-stu-id="5daa5-110">The container of all the nodes in the tree.</span></span> <span data-ttu-id="5daa5-111">Também é conhecido como diretório base, que nem sempre é o mesmo do elemento raiz.</span><span class="sxs-lookup"><span data-stu-id="5daa5-111">It is also known as the document root, which is not always the same as the root element.</span></span>|  
|<span data-ttu-id="5daa5-112">DocumentFragment</span><span class="sxs-lookup"><span data-stu-id="5daa5-112">DocumentFragment</span></span>|<xref:System.Xml.XmlDocumentFragment>|<span data-ttu-id="5daa5-113">Um recipiente temporário que contém um ou mais nós sem nenhuma estrutura de árvore.</span><span class="sxs-lookup"><span data-stu-id="5daa5-113">A temporary bag containing one or more nodes without any tree structure.</span></span>|  
|<span data-ttu-id="5daa5-114">DocumentType</span><span class="sxs-lookup"><span data-stu-id="5daa5-114">DocumentType</span></span>|<xref:System.Xml.XmlDocumentType>|<span data-ttu-id="5daa5-115">Representa o nó `<!DOCTYPE…>`.</span><span class="sxs-lookup"><span data-stu-id="5daa5-115">Represents the `<!DOCTYPE…>` node.</span></span>|  
|<span data-ttu-id="5daa5-116">EntityReference</span><span class="sxs-lookup"><span data-stu-id="5daa5-116">EntityReference</span></span>|<xref:System.Xml.XmlEntityReference>|<span data-ttu-id="5daa5-117">Representa o texto de referência de entidade não expandido.</span><span class="sxs-lookup"><span data-stu-id="5daa5-117">Represents the non-expanded entity reference text.</span></span>|  
|<span data-ttu-id="5daa5-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="5daa5-118">Element</span></span>|<xref:System.Xml.XmlElement>|<span data-ttu-id="5daa5-119">Representa um nó de elemento.</span><span class="sxs-lookup"><span data-stu-id="5daa5-119">Represents an element node.</span></span>|  
|<span data-ttu-id="5daa5-120">Attr</span><span class="sxs-lookup"><span data-stu-id="5daa5-120">Attr</span></span>|<xref:System.Xml.XmlAttribute>|<span data-ttu-id="5daa5-121">Atributo de um elemento.</span><span class="sxs-lookup"><span data-stu-id="5daa5-121">Is an attribute of an element.</span></span>|  
|<span data-ttu-id="5daa5-122">ProcessingInstruction</span><span class="sxs-lookup"><span data-stu-id="5daa5-122">ProcessingInstruction</span></span>|<xref:System.Xml.XmlProcessingInstruction>|<span data-ttu-id="5daa5-123">Nó de instrução de processamento.</span><span class="sxs-lookup"><span data-stu-id="5daa5-123">Is a processing instruction node.</span></span>|  
|<span data-ttu-id="5daa5-124">Comentário</span><span class="sxs-lookup"><span data-stu-id="5daa5-124">Comment</span></span>|<xref:System.Xml.XmlComment>|<span data-ttu-id="5daa5-125">Um nó de comentário.</span><span class="sxs-lookup"><span data-stu-id="5daa5-125">A comment node.</span></span>|  
|<span data-ttu-id="5daa5-126">Texto</span><span class="sxs-lookup"><span data-stu-id="5daa5-126">Text</span></span>|<xref:System.Xml.XmlText>|<span data-ttu-id="5daa5-127">Texto que pertence a um elemento ou a um atributo.</span><span class="sxs-lookup"><span data-stu-id="5daa5-127">Text belonging to an element or attribute.</span></span>|  
|<span data-ttu-id="5daa5-128">CDATASection</span><span class="sxs-lookup"><span data-stu-id="5daa5-128">CDATASection</span></span>|<xref:System.Xml.XmlCDataSection>|<span data-ttu-id="5daa5-129">Representa CDATA.</span><span class="sxs-lookup"><span data-stu-id="5daa5-129">Represents CDATA.</span></span>|  
|<span data-ttu-id="5daa5-130">Entidade</span><span class="sxs-lookup"><span data-stu-id="5daa5-130">Entity</span></span>|<xref:System.Xml.XmlEntity>|<span data-ttu-id="5daa5-131">Representa as declarações `<!ENTITY…>` em um documento XML, de um subconjunto de DTDs (definição de tipo de documento) internas ou de DTDs externas e de entidades de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5daa5-131">Represents the `<!ENTITY…>` declarations in an XML document, either from an internal document type definition (DTD) subset or from external DTDs and parameter entities.</span></span>|  
|<span data-ttu-id="5daa5-132">Notation</span><span class="sxs-lookup"><span data-stu-id="5daa5-132">Notation</span></span>|<xref:System.Xml.XmlNotation>|<span data-ttu-id="5daa5-133">Representa uma notação declarada na DTD.</span><span class="sxs-lookup"><span data-stu-id="5daa5-133">Represents a notation declared in the DTD.</span></span>|  
  
 <span data-ttu-id="5daa5-134">Mesmo que um atributo (*attr*) é listado no nível 1 do DOM do W3C seção 1.2 fundamentais Interfaces como um nó, ele não é considerado um filho de qualquer nó do elemento.</span><span class="sxs-lookup"><span data-stu-id="5daa5-134">Even though an attribute (*attr*) is listed in the W3C DOM Level 1 section 1.2 Fundamental Interfaces as a node, it is not considered a child of any element node.</span></span>  
  
 <span data-ttu-id="5daa5-135">A tabela a seguir mostra os tipos de nó adicional não definidos pelo W3C, mas eles estão disponíveis para uso no modelo de objeto do Microsoft .NET Framework como **XmlNodeType** enumerações.</span><span class="sxs-lookup"><span data-stu-id="5daa5-135">The following table shows additional node types not defined by the W3C, however they are available for use in the Microsoft .NET Framework object model as **XmlNodeType** enumerations.</span></span> <span data-ttu-id="5daa5-136">Portanto, não há nenhuma coluna de tipo de nó DOM correspondente com esses tipos de nós.</span><span class="sxs-lookup"><span data-stu-id="5daa5-136">Therefore, there is no matching DOM node type column for these node types.</span></span>  
  
|<span data-ttu-id="5daa5-137">Tipo de nó</span><span class="sxs-lookup"><span data-stu-id="5daa5-137">Node type</span></span>|<span data-ttu-id="5daa5-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="5daa5-138">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.Xml.XmlDeclaration>|<span data-ttu-id="5daa5-139">Representa o nó de declaração `<?xml version="1.0"…>`.</span><span class="sxs-lookup"><span data-stu-id="5daa5-139">Represents the declaration node `<?xml version="1.0"…>`.</span></span>|  
|<xref:System.Xml.XmlSignificantWhitespace>|<span data-ttu-id="5daa5-140">Representa o espaço em branco significativo, que é o espaço em branco com conteúdo misto.</span><span class="sxs-lookup"><span data-stu-id="5daa5-140">Represents significant white space, which is white space in mixed content.</span></span>|  
|<xref:System.Xml.XmlWhitespace>|<span data-ttu-id="5daa5-141">Representa o espaço em branco no conteúdo de um elemento.</span><span class="sxs-lookup"><span data-stu-id="5daa5-141">Represents the white space in the content of an element.</span></span>|  
|<span data-ttu-id="5daa5-142">EndElement</span><span class="sxs-lookup"><span data-stu-id="5daa5-142">EndElement</span></span>|<span data-ttu-id="5daa5-143">Retornado quando **XmlReader** obtém ao final de um elemento.</span><span class="sxs-lookup"><span data-stu-id="5daa5-143">Returned when **XmlReader** gets to the end of an element.</span></span><br /><br /> <span data-ttu-id="5daa5-144">Exemplo de XML:  **\< /item >**</span><span class="sxs-lookup"><span data-stu-id="5daa5-144">Example XML: **\</item>**</span></span><br /><br /> <span data-ttu-id="5daa5-145">Para obter mais informações, consulte <xref:System.Xml.XmlNodeType>.</span><span class="sxs-lookup"><span data-stu-id="5daa5-145">For more information, see <xref:System.Xml.XmlNodeType>.</span></span>|  
|<span data-ttu-id="5daa5-146">EndEntity</span><span class="sxs-lookup"><span data-stu-id="5daa5-146">EndEntity</span></span>|<span data-ttu-id="5daa5-147">Retornado quando **XmlReader** chegar ao fim da substituição de entidade como resultado de uma chamada para <xref:System.Xml.XmlReader.ResolveEntity%2A>.</span><span class="sxs-lookup"><span data-stu-id="5daa5-147">Returned when **XmlReader** gets to the end of the entity replacement as a result of a call to <xref:System.Xml.XmlReader.ResolveEntity%2A>.</span></span> <span data-ttu-id="5daa5-148">Para obter mais informações, consulte <xref:System.Xml.XmlNodeType>.</span><span class="sxs-lookup"><span data-stu-id="5daa5-148">For more information, see <xref:System.Xml.XmlNodeType>.</span></span>|  
  
 <span data-ttu-id="5daa5-149">Para ver um exemplo de código que lê em XML e usa uma construção caso os tipos de nó para imprimir informações sobre o nó e seu conteúdo, consulte <xref:System.Xml.XmlSignificantWhitespace.NodeType%2A>.</span><span class="sxs-lookup"><span data-stu-id="5daa5-149">To view a code example that reads in XML and uses a case construct on the node types to print information about the node and its contents, see <xref:System.Xml.XmlSignificantWhitespace.NodeType%2A>.</span></span>  
  
 <span data-ttu-id="5daa5-150">Para obter mais informações sobre a hierarquia de objetos dos tipos de nó e o nome do objeto equivalente, consulte [hierarquia de modelo de objeto de documento (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="5daa5-150">For more information on the object hierarchy of the node types and their equivalent object name, see [XML Document Object Model (DOM) Hierarchy](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md).</span></span> <span data-ttu-id="5daa5-151">Para obter mais informações sobre os objetos criados na árvore de nós, consulte [mapeando a hierarquia de objetos para dados XML](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="5daa5-151">For more information on the objects created in the node tree, see [Mapping the Object Hierarchy to XML Data](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5daa5-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5daa5-152">See Also</span></span>  
 [<span data-ttu-id="5daa5-153">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="5daa5-153">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)