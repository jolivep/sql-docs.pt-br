---
title: Elemento Row (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- row Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#row
- microsoft.xml.analysis.row
- http://schemas.microsoft.com/analysisservices/2003/engine#row
helpviewer_keywords:
- row element
ms.assetid: 4d9977a0-c396-44c7-9fd4-97f4c3d643aa
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: de6460bc6d51c4205752b7db186412e420438145
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36011458"
---
# <a name="row-element-xmla"></a>Elemento row (XMLA)
  Contém uma única linha de dados para um [raiz](root-element-xmla.md) elemento que contém dados tabulares retornados por uma [Discover](../xml-elements-methods-discover.md) ou [Execute](../xml-elements-methods-execute.md) chamada de método.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <row>  
      <!-- One or more column elements -->  
   </row>  
</root>  
```  
  
## <a name="element-characteristics"></a>Características do elemento  
  
|Característica|Description|  
|--------------------|-----------------|  
|Comprimento e tipo de dados|Nenhum|  
|Valor padrão|Nenhum|  
|Cardinalidade|0-n: Elemento opcional que pode ocorrer mais de uma vez.|  
  
## <a name="element-relationships"></a>Relações do elemento  
  
|Relação|Elemento|  
|------------------|-------------|  
|Elementos pai|[raiz](root-element-xmla.md) (usando o [linhas](../xml-data-types/rowset-data-type-xmla.md) tipo de dados)|  
|Elementos filho|Um ou mais elementos de coluna.|  
  
## <a name="remarks"></a>Remarks  
 Cada linha retornada por um elemento `root` que contém dados tabulares tem um elemento `row` correspondente. Cada coluna no elemento `root` é representada por um elemento XML separado. O valor da coluna para o elemento `row` equivale aos dados contidos pelo elemento XML e o nome da coluna corresponde ao nome do elemento XML.  
  
 Há dois modos para expressar um valor nulo para uma coluna em uma linha:  
  
-   Um elemento de coluna ausente indica que a coluna é nula.  
  
-   O elemento de coluna pode usar o atributo `xsi:nil='true'` para indicar que tem um valor nulo.  
  
 Por exemplo, se uma linha tiver uma única coluna chamada Store_Name e seu valor for NULL, ela poderá ser representada como:  
  
```  
<row>  
</row>  
```  
  
 Ou:  
  
```  
<row>  
   <Store_name xsi:nil='true'/>  
</row>  
```  
  
 Se um elemento de coluna contiver um erro, um elemento `Error` fornecerá informações sobre o erro, conforme descrito no exemplo a seguir:  
  
```  
<row>   <Store_name>  
      <Error xmlns="urn:schemas-microsoft-com:xml-analysis:exception">  
         <ErrorCode>3238658054</ErrorCode>  
         <Description>The object [X] was not found in the cube when [X] was parsed.</Description>  
      </Error>  
   </Store_name>  
</row>  
```  
  
 Para obter mais informações sobre nomes de coluna e informações de esquema para dados de tabela, consulte [tipo de dados do conjunto de linhas &#40;XMLA&#41;](../xml-data-types/rowset-data-type-xmla.md).  
  
## <a name="see-also"></a>Consulte também  
 [Propriedades &#40;XMLA&#41;](xml-elements-properties.md)  
  
  