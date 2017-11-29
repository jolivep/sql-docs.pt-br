---
title: sp_help_log_shipping_monitor_primary (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_log_shipping_monitor_primary
- sp_help_log_shipping_monitor_primary_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_help_log_shipping_monitor_primary
ms.assetid: d9dfcb8f-1da6-49ca-a2c8-411574915434
caps.latest.revision: "21"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 60b7efa0b08c52785b95e31ab06750da051002e5
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="sphelplogshippingmonitorprimary-transact-sql"></a>sp_help_log_shipping_monitor_primary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retorna informações relativas a um banco de dados primário a partir das tabelas de monitor.  
  
||  
|-|  
|**Aplica-se a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] até a [versão atual](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Ícone de link do tópico](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Convenções da sintaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
sp_help_log_shipping_monitor_primary  
[ @primary_server = ] 'primary_server',   
[ @primary_database = ] 'primary_database'  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@primary_server =** ] '*primary_server*'  
 O nome da instância primária do [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] na configuração de envio de logs. *primary_server* é **sysname** e não pode ser NULL.  
  
 [  **@primary_database =** ] '*primary_database*'  
 É o nome do banco de dados do servidor primário. *primary_database* é **sysname**, sem padrão.  
  
## <a name="return-code-values"></a>Valores do código de retorno  
 0 (êxito) ou 1 (falha)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nome da coluna|Description|  
|-----------------|-----------------|  
|**primary_id**|A ID do banco de dados primário para a configuração de envio de log.|  
|**primary_server**|Nome da instância primária do [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] na configuração de envio de logs.|  
|**primary_database**|O nome do banco de dados primário na configuração de envio de log.|  
|**backup_threshold**|O número de minutos permitidos a decorrer entre operações de backup antes que um alerta seja gerado.|  
|**alerta de limite**|O alerta a ser emitido quando o limite do backup for excedido.|  
|**threshold_alert_enabled**|Determina se os alertas de limite de backup foram habilitados. 1 = habilitado; 0 = desabilitado.|  
|**colunas last_backup_file**|O caminho absoluto de backup de log de transações mais recente.|  
|**last_backup_date**|A hora e data da última operação de backup de log de transações no banco de dados primário.|  
|**last_backup_date_utc**|A hora e data da última operação de backup de log de transação no banco de dados primário, expressas no Tempo Universal Coordenado.|  
|**history_retention_period**|A quantidade de tempo, em minutos, que os registros do histórico do envio de log são mantidos para um determinado banco de dados primário antes de serem excluídos.|  
  
## <a name="remarks"></a>Comentários  
 **sp_help_log_shipping_monitor_primary** deve ser executado a partir de **mestre** banco de dados no servidor monitor.  
  
## <a name="permissions"></a>Permissões  
 Somente membros do **sysadmin** função fixa de servidor pode executar esse procedimento.  
  
## <a name="see-also"></a>Consulte também  
 [Sobre o envio de logs &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Procedimentos armazenados do sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  