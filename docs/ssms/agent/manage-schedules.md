---
title: Gerenciar agendas | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.manageschedules.f1
ms.assetid: f56c0736-dccc-41d2-afcf-71344aff143a
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: d193c516566635bae1cfba0d691f823b2cba5d31
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68257821"
---
# <a name="manage-schedules"></a>Gerenciar Agendas
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> No momento, na [Instância Gerenciada do Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), a maioria dos recursos do SQL Server Agent é compatível, mas não todos. Consulte [Azure SQL Database Managed Instance T-SQL differences from SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent) (Diferenças entre o T-SQL da Instância Gerenciada do Banco de Dados SQL do Azure e o SQL Server) para obter detalhes.

Permite exibir e alterar as propriedades das agendas de trabalho do [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="options"></a>Opções  
**Agendas disponíveis**  
Exibe as agendas disponíveis para este usuário. Observe que um trabalho e uma agenda devem ter o mesmo proprietário. Portanto, esta lista só inclui agendas pertencentes ao proprietário do trabalho.  
  
**Nome**  
Exibe o nome da agenda.  
  
**Enabled**  
Selecione esta opção para habilitar a agenda.  
  
**Descrição**  
Descreve as condições em que a agenda executa o trabalho.  
  
**Trabalhos na agenda**  
Exibe os números de trabalhos anexados à agenda. Clique em um número para exibir as propriedades do trabalho.  
  
**Nova**  
Clique neste botão para criar uma agenda nova.  
  
**Delete (excluir)**  
Clique neste botão para excluir a agenda selecionada.  
  
**Propriedades**  
Clique neste botão para alterar as propriedades da agenda selecionada.  
  
## <a name="see-also"></a>Consulte Também  
[Criar e anexar agendas para trabalhos](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
  
