---
title: Analisar deadlocks com SQL Server Profiler | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- process nodes [SQL Server Profiler]
- Profiler [SQL Server Profiler], deadlocks
- deadlocks [SQL Server], identifying cause
- resource nodes [SQL Server Profiler]
- graphs [SQL Server Profiler]
- SQL Server Profiler, deadlocks
- events [SQL Server], deadlocks
- edges [SQL Server Profiler]
ms.assetid: 72d6718f-501b-4ea6-b344-c0e653f19561
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ca1882faa9c61536d1ef025058322f141beedafd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63316325"
---
# <a name="analyze-deadlocks-with-sql-server-profiler"></a>Analisar deadlocks com o SQL Server Profiler
  Use o [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] para identificar a causa de um deadlock. Um deadlock ocorre quando há uma dependência cíclica entre dois ou mais threads, ou processos, do mesmo conjunto de recursos dentro do SQL Server. Usando o [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], é possível criar um rastreamento que registra, reproduz e exibe eventos de deadlock para análise.  
  
 Para rastrear eventos de deadlock, adicione a classe de evento **Deadlock graph** a um rastreamento. Esta classe de evento popula a coluna de dados **TextData** no rastreamento com dados XML sobre o processo e objetos que estão envolvidos no deadlock. 
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pode extrair o documento XML para um arquivo XML de deadlock (.xdl) que pode ser exibido posteriormente no SQL Server Management Studio. Você pode configurar o [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] para extrair eventos **Deadlock graph** para um único arquivo contendo todos os eventos **Deadlock graph** ou para arquivos separados. Essa extração pode ser feita de qualquer uma destas formas:  
  
-   No momento da configuração de rastreamento, usando a guia **configurações de extração de eventos** . Observe que essa guia não aparece até que você selecione o evento do **grafo de deadlock** na guia Seleção de **eventos** .  
  
-   Usando a opção **Extrair Eventos do SQL Server** no menu **Arquivo** .  
  
-   Eventos individuais também podem ser extraídos e salvos clicando com o botão direito do mouse em um evento específico e escolhendo **Extrair Dados de Evento**.  
  
## <a name="deadlock-graphs"></a>Gráficos de deadlock  
 
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] e o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] usam um gráfico de espera de deadlock para descrever um deadlock. O gráfico de espera de deadlock contém nós de processo, nós de recurso e bordas representando as relações entre os processos e os recursos. Os componentes dos gráficos de espera estão definidos na tabela a seguir:  
  
 Nó de processo  
 Um thread que executa uma tarefa; por exemplo, INSERT, UPDATE ou DELETE.  
  
 Nó de recurso  
 Um objeto de banco de dados; por exemplo, uma tabela, índice ou linha.  
  
 Microsoft Edge  
 Uma relação entre um processo e um recurso. Uma borda `request` ocorre quando um processo espera por um recurso. Uma borda `owner` ocorre quando um recurso espera por um processo. O modo de bloqueio encontra-se na descrição da borda. Por exemplo, **Modo: X**.  
  
## <a name="deadlock-process-node"></a>Nó de processo de deadlock  
 Em um gráfico de espera, o nó de processo contém informações sobre o processo. A tabela a seguir explica os componentes de um processo.  
  
|Componente|Definição|  
|---------------|----------------|  
|ID de processo do servidor|Identificador de processo de servidor (SPID), um identificador atribuído pelo servidor ao processo proprietário do bloqueio.|  
|ID de lote do servidor|Identificador de lote de servidor (SBID).|  
|ID do contexto de execução|Identificador do contexto de execução (ECID). A ID do contexto de execução de determinado thread associado a uma SPID específica.<br /><br /> ECID = {0,1,2,3, *...n*}, em que 0 sempre representa o thread principal ou pai e {1,2,3, *...n*} representa os subthreads.|  
|Prioridade do deadlock|Prioridade do deadlock para o processo. Para obter mais informações sobre os valores possíveis, veja [SET DEADLOCK_PRIORITY &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-deadlock-priority-transact-sql).|  
|Log Usado|Quantidade de espaço de log usada pelo processo.|  
|ID do Proprietário|ID de transação para os processos que estão usando transações e, atualmente, aguardam em um bloqueio.|  
|Descritor da transação|Ponteiro para o descritor de transação que descreve o estado da transação.|  
|Buffer de entrada|Buffer de entrada do processo atual; define o tipo de evento e a instrução que são executados. Os valores possíveis incluem:<br /><br /> **Idioma**<br /><br /> **RPC**<br /><br /> **Nenhuma**|  
|de|Tipo de instrução. Os valores possíveis são:<br /><br /> **NOP**<br /><br /> **SELECT**<br /><br /> **UPDATE**<br /><br /> **INSERT**<br /><br /> **DELETE**<br /><br /> **Conhecidos**|  
  
## <a name="deadlock-resource-node"></a>Nó de recurso de deadlock  
 Em um deadlock, dois processos esperam por um recurso ocupado pelo outro processo. Em um gráfico de deadlock, os recursos são exibidos como nós de recurso.  
  
  
