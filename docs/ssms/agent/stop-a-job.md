---
title: Parar um trabalho   Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
ms.assetid: 4249328a-24d8-4284-9d1d-7d04ed90e3d7
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: baeca9415080f7b333e2edbe55f447d1017a9f2e
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265219"
---
# <a name="stop-a-job"></a>Stop a Job
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> No momento, na [Instância Gerenciada do Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), a maioria dos recursos do SQL Server Agent é compatível, mas não todos. Consulte [Azure SQL Database Managed Instance T-SQL differences from SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent) (Diferenças entre o T-SQL da Instância Gerenciada do Banco de Dados SQL do Azure e o SQL Server) para obter detalhes.

Este tópico descreve como interromper um trabalho do [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Um trabalho é uma série especificada de ações que o SQL Server Agent executa.  
  
-   **Antes de começar:**  ,  
  
    [Limitações e restrições](#Restrictions)  
  
    [Segurança](#Security)  
  
-   **Para interromper um trabalho usando:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Antes de começar  
  
### <a name="Restrictions"></a>Limitações e restrições  
  
-   Se um trabalho estiver executando no momento uma etapa do tipo **CmdExec** ou **PowerShell**, o processo em execução (por exemplo, MyProgram.exe) será forçado a terminar prematuramente. Isso pode causar comportamento imprevisível, como manter abertos os arquivos em uso pelo processo.  
  
-   Em caso de trabalho multisservidor, uma instrução STOP para o trabalho é postada em todos os servidores de destino do trabalho.  
  
### <a name="Security"></a>Segurança  
Para obter informações detalhadas, consulte [Implementar a segurança do SQL Server Agent](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Usando o SQL Server Management Studio  
  
#### <a name="to-stop-a-job"></a>Para interromper um trabalho  
  
1.  No **Pesquisador de Objetos** , conecte-se a uma instância do [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]e a expanda.  
  
2.  Expanda **SQL Server Agent**, expanda **Trabalhos**, clique com o botão direito do mouse no trabalho que deseja interromper e clique em **Parar Trabalho**.  
  
3.  Se desejar interromper vários trabalhos, clique com o botão direito do mouse em **Monitor de Atividade do Trabalho**e, depois, clique em **Exibir Atividade do Trabalho**. No Monitor de Atividade do Trabalho, selecione os trabalhos que você deseja interromper, clique com o botão direito do mouse em sua seleção e, depois, clique em **Parar Trabalhos**.  
  
## <a name="TSQL"></a>Usando Transact-SQL  
  
#### <a name="to-stop-a-job"></a>Para interromper um trabalho  
  
1.  No **Pesquisador de Objetos**, conecte-se a uma instância do [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Na barra Padrão, clique em **Nova Consulta**.  
  
3.  Copie e cole o exemplo a seguir na janela de consulta e clique em **Executar**.  
  
    ```  
    -- stops a job named Weekly Sales Data Backup  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_stop_job  
        N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
Para obter mais informações, consulte [sp_stop_job (Transact-SQL)](https://msdn.microsoft.com/64b4cc75-99a0-421e-b418-94e37595bbb0).  
  
## <a name="SMO"></a>Usando o SQL Server Management Objects  
**Para interromper um trabalho**  
  
Chame o método **Stop** da classe **Job** usando uma linguagem de programação à sua escolha, como Visual Basic, Visual C# ou PowerShell. Para obter mais informações, veja [SMO (SQL Server Management Objects)](https://msdn.microsoft.com/library/ms162169.aspx).  
  
