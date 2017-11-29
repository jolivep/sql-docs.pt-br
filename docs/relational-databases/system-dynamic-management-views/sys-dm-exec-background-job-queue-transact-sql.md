---
title: exec_background_job_queue (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_exec_background_job_queue
- sys.dm_exec_background_job_queue_TSQL
- dm_exec_background_job_queue_TSQL
- sys.dm_exec_background_job_queue
dev_langs: TSQL
helpviewer_keywords: sys.dm_exec_background_job_queue dynamic management function
ms.assetid: 05d9884f-b74c-4e3c-a23b-c90c1ea5ef02
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a19fc2817900e8f3c2e618296d650ac92ec2b6fa
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmexecbackgroundjobqueue-transact-sql"></a>sys.dm_exec_background_job_queue (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retorna uma linha para cada trabalho de processador de consulta agendado para execução assíncrona (em segundo plano).  
  
> **OBSERVAÇÃO!** Para chamar essa de  **[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]**  ou  **[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]** , use o nome **sys.dm_pdw_nodes_exec_background_job_queue**.  
  
|Nome da coluna|Tipo de dados|Description|  
|-----------------|---------------|-----------------|  
|**time_queued**|**datetime**|Hora em que a tarefa foi adicionada à fila.|  
|**job_id**|**int**|Job identifier.|  
|**database_id**|**int**|Banco de dados no qual a tarefa será executada.|  
|**object_id1**|**int**|O valor depende do tipo de trabalho. Para obter mais informações, consulte a seção Comentários.|  
|**object_id2**|**int**|O valor depende do tipo de trabalho. Para obter mais informações, consulte a seção Comentários.|  
|**object_id3**|**int**|O valor depende do tipo de trabalho. Para obter mais informações, consulte a seção Comentários.|  
|**object_id4**|**int**|O valor depende do tipo de trabalho. Para obter mais informações, consulte a seção Comentários.|  
|**error_code**|**int**|Código de erro se o trabalho for reinserido devido à falha. NULL se suspenso, não coletado ou concluído.|  
|**request_type**|**smallint**|Tipo de solicitação de trabalho.|  
|**contagem_novas_tentativas**|**smallint**|Número de vezes que o trabalho foi coletado da fila e reinserido devido à falta de recursos ou outros motivos.|  
|**in_progress**|**smallint**|Indica se o trabalho iniciou a execução.<br /><br /> 1 = Iniciado<br /><br /> 0 = Ainda esperando|  
|**session_id**|**smallint**|Identificador de sessão.|  
|**pdw_node_id**|**int**|**Aplica-se a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> O identificador para o nó que essa distribuição é no.|  
  
## <a name="permissions"></a>Permissões  
 Em [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requer a permissão VIEW SERVER STATE no servidor.  
  
 Em [!INCLUDE[ssSDS](../../includes/sssds-md.md)] camadas Premium requer a permissão VIEW DATABASE STATE no banco de dados. Em [!INCLUDE[ssSDS](../../includes/sssds-md.md)] camadas Standard e Basic requer o [!INCLUDE[ssSDS](../../includes/sssds-md.md)] conta de administrador.  
  
## <a name="remarks"></a>Comentários  
 Esta exibição só retorna informações para trabalhos de estatísticas de atualizações assíncronas. Para obter mais informações sobre atualização assíncrona de estatísticas, consulte [estatísticas](../../relational-databases/statistics/statistics.md).  
  
 Os valores de **object_id1** por meio de **object_id4** dependem do tipo da solicitação de trabalho. A tabela a seguir resume o significado dessas colunas para os diferentes tipos de trabalho.  
  
|Tipo de solicitação|object_id1|object_id2|object_id3|object_id4|  
|------------------|-----------------|-----------------|-----------------|-----------------|  
|Estatísticas de atualização assíncrona|Tabela ou ID de exibição|ID de estatísticas|Não usado|Não usado|  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir retorna o número de trabalhos assíncronos ativos na fila em segundo plano para cada banco de dados na instância de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
SELECT DB_NAME(database_id) AS [Database], COUNT(*) AS [Active Async Jobs]  
FROM sys.dm_exec_background_job_queue  
WHERE in_progress = 1  
GROUP BY database_id;  
GO  
```  
  
## <a name="see-also"></a>Consulte também  
 [Exibições e funções de gerenciamento dinâmico &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Funções e exibições de gerenciamento dinâmico &#40; relacionadas à execução Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Estatísticas](../../relational-databases/statistics/statistics.md)   
 [KILL STATS JOB &#40; Transact-SQL &#41;](../../t-sql/language-elements/kill-stats-job-transact-sql.md)  
  
  


