---
title: Método SaveToFile | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_SaveToFile
- _Stream::SaveToFile
helpviewer_keywords:
- SaveToFile method [ADO]
ms.assetid: 8a8594f2-422b-4d2e-94f8-7fe337445900
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c2e56178ad306d5b39c2445c391c3bbabe4fc424
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67917029"
---
# <a name="savetofile-method"></a>Método SaveToFile
Salva o conteúdo binário de um [fluxo](../../../ado/reference/ado-api/stream-object-ado.md) em um arquivo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Stream.SaveToFile FileName, SaveOptions  
```  
  
#### <a name="parameters"></a>parâmetros  
 *Nome do arquivo*  
 Um valor de **cadeia de caracteres** que contém o nome totalmente qualificado do arquivo para o qual o conteúdo do **fluxo** será salvo. Você pode salvar em qualquer local local válido ou em qualquer local ao qual tenha acesso por meio de um valor UNC.  
  
 *Salvaroptions*  
 Um valor de [SaveOptionsEnum](../../../ado/reference/ado-api/saveoptionsenum.md) que especifica se um novo arquivo deve ser criado pelo **SaveToFile**, caso ainda não exista. O valor padrão é **adSaveCreateNotExists**. Com essas opções, você pode especificar que um erro ocorrerá se o arquivo especificado não existir. Você também pode especificar que o **SaveToFile** substitui o conteúdo atual de um arquivo existente.  
  
> [!NOTE]
>  Se você substituir um arquivo existente (quando **adSaveCreateOverwrite** estiver definido), **SaveToFile** truncará todos os bytes do arquivo original existente que seguem o novo [EOS](../../../ado/reference/ado-api/eos-property.md).  
  
## <a name="remarks"></a>Comentários  
 **SaveToFile** pode ser usado para copiar o conteúdo de um objeto de **fluxo** para um arquivo local. Não há nenhuma alteração no conteúdo ou nas propriedades do objeto de **fluxo** . O objeto de **fluxo** deve ser aberto antes de chamar **SaveToFile**.  
  
 Esse método não altera a associação do objeto de **fluxo** para sua fonte subjacente. O objeto de **fluxo** ainda será associado à URL ou ao **registro** original que foi sua origem quando aberto.  
  
 Após uma operação **SaveToFile** , a posição atual ([posição](../../../ado/reference/ado-api/position-property-ado.md)) no fluxo é definida como o início do fluxo (0).  
  
## <a name="applies-to"></a>Aplica-se A  
 [Objeto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Consulte Também  
 [Método Open (fluxo ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Método Save](../../../ado/reference/ado-api/save-method.md)
