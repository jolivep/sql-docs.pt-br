---
title: Método WriteText | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_WriteText
- _Stream::WriteText
helpviewer_keywords:
- WriteText method [ADO]
ms.assetid: 7a669048-13f4-4574-a2b1-985e089729d5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 64b7d8fd3f2220562e3695d6e31c83261daa2e60
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67947492"
---
# <a name="writetext-method"></a>Método WriteText
Grava uma cadeia de caracteres de texto especificada em um objeto de [fluxo](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Stream.WriteText Data, Options  
```  
  
#### <a name="parameters"></a>parâmetros  
 *Dados*  
 Um valor de **cadeia de caracteres** que contém o texto em caracteres a ser gravado.  
  
 *Opções*  
 Opcional. Um valor [StreamWriteEnum](../../../ado/reference/ado-api/streamwriteenum.md) que especifica se um caractere separador de linha deve ser gravado no final da cadeia de caracteres especificada.  
  
## <a name="remarks"></a>Comentários  
 As cadeias de caracteres especificadas são gravadas no objeto de **fluxo** sem nenhum espaço ou caractere intermediário entre cada cadeia de caracteres.  
  
 A [posição](../../../ado/reference/ado-api/position-property-ado.md) atual é definida como o caractere após os dados gravados. O método **WriteText** não trunca o restante dos dados em um fluxo. Se você quiser truncar esses caracteres, chame [SetEOS](../../../ado/reference/ado-api/seteos-method.md).  
  
 Se você gravar após a posição de [EOS](../../../ado/reference/ado-api/eos-property.md) atual, o [tamanho](../../../ado/reference/ado-api/size-property-ado-stream.md) do **fluxo** será aumentado para conter os novos caracteres e o **EOS** será movido para o novo último byte no **fluxo**.  
  
> [!NOTE]
>  O método **WriteText** é usado com fluxos de texto (o[tipo](../../../ado/reference/ado-api/type-property-ado-stream.md) é **adTypeText**). Para fluxos binários (o**tipo** é **adTypeBinary**), use [Write](../../../ado/reference/ado-api/write-method.md).  
  
## <a name="applies-to"></a>Aplica-se A  
 [Objeto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Consulte Também  
 [Método Write](../../../ado/reference/ado-api/write-method.md)
