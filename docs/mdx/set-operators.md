---
title: Definir operadores | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6ad0b92a970c3618584365d9ad6e99420daef05d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037015"
---
# <a name="set-operators"></a>Operadores de conjunto


  Na linguagem MDX, os operadores de conjunto executam operações em membros ou conjuntos e retornam um conjunto. Frequentemente você usa os operadores de conjunto como uma alternativa para várias funções de conjunto na linguagem MDX.  
  
 O MDX oferece suporte a operadores de conjunto listados na tabela a seguir.  
  
|Operador|DESCRIÇÃO|  
|--------------|-----------------|  
|[-(Exceto)](../mdx/except-mdx-operator.md)|Retorna a diferença entre dois conjuntos, removendo membros duplicados.<br /><br /> Esse operador é funcionalmente equivalente à função [Except](../mdx/except-mdx-function.md) .|  
|[* (Interjunção)](../mdx/crossjoin-mdx-operator-reference.md)|Retorna o produto cruzado de dois conjuntos.<br /><br /> Esse operador é funcionalmente equivalente à função de [interjunção](../mdx/crossjoin-mdx.md) .|  
|[: (Intervalo)](../mdx/range-mdx.md)|Retorna um conjunto ordenado naturalmente, com dois membros especificados como pontos de extremidade, e todos os membros entre os dois membros especificados incluídos como membros do conjunto.|  
|[+ (Union)](../mdx/union-mdx-operator-reference.md)|Retorna uma união de dois conjuntos, exceto membros duplicados.<br /><br /> Esse operador é funcionalmente equivalente à função [Union &#40;MDX&#41;](../mdx/union-mdx.md) .|  
  
## <a name="see-also"></a>Consulte Também  
 [Referência de função MDX &#40;&#41;MDX](../mdx/mdx-function-reference-mdx.md)   
 [Referência de operador MDX &#40;&#41;MDX](../mdx/mdx-operator-reference-mdx.md)   
 [Operadores &#40;sintaxe MDX&#41;](../mdx/operators-mdx-syntax.md)  
  
  
