---
title: MSSQLSERVER_41333 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41333 (Database Engine error)
ms.assetid: c3c3ae9a-1e4c-4de6-ba72-2f393375b053
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ab94977bcd3bf5a9b0b26ac7be76cb67d58e0755
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62913982"
---
# <a name="mssqlserver_41333"></a>MSSQLSERVER_41333
    
## <a name="details"></a>Detalhes  
  
|||  
|-|-|  
|Nome do Produto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID do evento|41333|  
|Origem do Evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbólico|CROSS_CONTAINER_ISOLATION_FAILURE|  
|Texto da mensagem|As transações a seguir devem acessar tabelas com otimização de memória e procedimentos armazenados compilados nativamente no isolamento de instantâneo: as transações RepeatableRead, as transações Serializable e as transações que acessam tabelas que não têm otimização de memória no isolamento RepeatableRead ou Serializable.|  
  
## <a name="explanation"></a>Explicação  
 Há restrições relacionadas ao usuário dos níveis de isolamento mais altos entre transações baseadas em disco e transações XTP.  
  
## <a name="user-action"></a>Ação do usuário  
 Não tente operações de alto nível de isolamento em tabelas com otimização de memória (e em procedimentos originalmente compilados) e tabelas baseadas em disco.  
  
 Para obter mais informações, veja [OLTP in-memory &#40;Otimização na memória&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Consulte Também  
 [OLTP in-memory &#40;Otimização na memória&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
