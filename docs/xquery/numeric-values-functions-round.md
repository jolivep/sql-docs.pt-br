---
title: Função Round (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:round function
- round function [XQuery]
ms.assetid: 320b572f-bd5b-4055-95a6-dec5718c0041
author: rothja
ms.author: jroth
ms.openlocfilehash: 1927d6e483683699196cfc7e87928f27bf23446a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67946540"
---
# <a name="numeric-values-functions---round"></a>Funções de Valores Numéricos – round
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Retorna o número que não tem uma parte fracionária mais próxima do argumento. Se houver mais de um número semelhante a esse, o que for mais próximo ao infinito positivo será retornado. Por exemplo:  
  
 Se o argumento for 2,5, **Round ()** retornará 3.  
  
 Se o argumento for 2,4999, **Round ()** retornará 2.  
  
 Se o argumento for-2,5, **Round ()** retornará-2.  
  
 Se o argumento for uma sequência vazia, **Round ()** retornará a sequência vazia.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
fn:round ( $arg as numeric?) as numeric?  
```  
  
## <a name="arguments"></a>Argumentos  
 *$arg*  
 Número ao qual a função é aplicada.  
  
## <a name="remarks"></a>Comentários  
 Se o tipo de *$ARG* for um dos três tipos de base numéricos, **xs: float**, **xs: Double**ou **xs: decimal**, o tipo de retorno será o mesmo que o tipo de *$ARG* . Se o tipo de *$ARG* for um tipo derivado de um dos tipos numéricos, o tipo de retorno será o tipo numérico base.  
  
 Se a entrada nas funções **fn: Floor**, **fn: teto**ou **fn: round** for **xdt: untypedAtomic**, dados não tipados, ela será convertida implicitamente em **xs: Double**.  
  
 Qualquer outro tipo gera um erro estático.  
  
## <a name="examples"></a>Exemplos  
 Este tópico fornece exemplos de XQuery em relação a instâncias XML armazenadas em várias colunas de tipo **XML** no banco de dados AdventureWorks.  
  
 Você pode usar o exemplo de trabalho na [função de teto (XQuery)](../xquery/numeric-values-functions-ceiling.md) para a função **Round ()** XQuery. Tudo o que você precisa fazer é substituir a função de **teto ()** na consulta pela função **Round ()** .  
  
## <a name="implementation-limitations"></a>Limitações de implementação  
 Estas são as limitações:  
  
-   A função **Round ()** mapeia valores inteiros para xs: decimal.  
  
-   A função **Round ()** dos valores xs: Double e xs: float entre-0,5 E0 e-0e0 são mapeadas para 0e0 em vez de-0e0.  
  
## <a name="see-also"></a>Consulte Também  
 [Função Floor &#40;&#41;XQuery](../xquery/numeric-values-functions-floor.md)   
 [Função de teto &#40;&#41;XQuery](../xquery/numeric-values-functions-ceiling.md)  
  
  
