---
title: sys.dm_pdw_component_health_active_alerts (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c53e4a36-b841-424a-b8e2-255b1878deb6
caps.latest.revision: "8"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c88fd88a8545e5fa375732377f0afdbf92b70f96
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmpdwcomponenthealthactivealerts-transact-sql"></a>sys.dm_pdw_component_health_active_alerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Armazena alertas ativos em [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] componentes.  
  
|Nome da coluna|Tipo de dados|Description|Intervalo|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Identificador exclusivo de um [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] nó.<br /><br /> pdw_node_id, identificação_do_componente, component_instance_id, alert_id e alert_instance_id formam a chave para este modo de exibição.|NOT NULL|  
|identificação_do_componente|**int**|A ID do componente. Consulte [sys.pdw_health_components &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> pdw_node_id, identificação_do_componente, component_instance_id, alert_id e alert_instance_id formam a chave para este modo de exibição.|NOT NULL|  
|component_instance_id|**nvarchar(255)**|pdw_node_id, identificação_do_componente, component_instance_id, alert_id e alert_instance_id formam a chave para este modo de exibição.|NOT NULL|  
|alert_id|**int**|A ID para o tipo de alerta. Consulte [sys.pdw_health_alerts &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md).<br /><br /> pdw_node_id, identificação_do_componente, component_instance_id, alert_id e alert_instance_id formam a chave para este modo de exibição.|NOT NULL|  
|alert_instance_id|**nvarchar(36)**|Identifica uma instância de um determinado alerta.<br /><br /> pdw_node_id, identificação_do_componente, component_instance_id, alert_id e alert_instance_id formam a chave para este modo de exibição.|NOT NULL|  
|current_value|**nvarchar(255)**|Usado quando o alerta é do tipo StatusChange. Este é o status atual do componente. Valor é NULL para alertas do tipo de limite. Consulte [sys.pdw_health_alerts &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) para obter uma lista de tipos de alertas.|NULL|  
|previous_value|**nvarchar(255)**|Usado quando o alerta é do tipo StatusChange. Este é o status do componente anterior. Valor é NULL para alertas do tipo de limite. Consulte [sys.pdw_health_alerts &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md) para obter uma lista de tipos de alertas.|NULL|  
|create_time|**datetime**|Hora e data em que o alerta foi gerado.|NOT NULL|  
  
 Para obter informações sobre o máximo de linhas mantido por esta exibição, consulte "Mínimo e máximo valores" a [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [SQL Data Warehouse e exibições de gerenciamento dinâmico do Parallel Data Warehouse &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  