---
title: Renomear uma instância do cluster de failover do SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- clusters [SQL Server], virtual servers
- renaming virtual servers
- virtual servers [SQL Server], failover clustering
- failover clustering [SQL Server], virtual servers
ms.assetid: 2a49d417-25fb-4760-8ae5-5871bfb1e6f3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4ce98bacfcc5f3aa8814a9253d1796fd18c4a735
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63125991"
---
# <a name="rename-a-sql-server-failover-cluster-instance"></a>Renomear uma instância do cluster de failover do SQL Server
  Quando uma instância do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fizer parte de um cluster de failover, o processo de renomeação do servidor virtual diferirá da renomeação de uma instância autônoma. Para obter mais informações, consulte [Renomear um computador que hospeda uma instância autônoma do SQL Server](../../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md).  
  
 O nome do servidor virtual sempre será igual ao nome do Nome de Rede do SQL (o Nome de Rede do Servidor Virtual SQL). Embora você possa alterar o nome do servidor virtual, você não pode alterar o nome da instância. Por exemplo, você pode alterar um servidor virtual chamado VS1\instance1 para algum outro nome, como SQL35\instance1, mas a parte da instância do nome, instance1, permanecerá inalterada.  
  
 Antes de começar o processo de renomeação, revise os itens a seguir.  
  
-   
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] não dá suporte à renomeação de servidores envolvidos na replicação, exceto no caso de uso de envio de logs com a replicação. O servidor secundário no envio de logs poderá ser renomeado se o servidor primário for permanentemente perdido. Para obter mais informações, veja [Replicação e envio de logs &#40;SQL Server&#41;](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md).  
  
-   Quando você renomear um servidor virtual que está configurado para usar espelhamento de banco de dados, deverá desativar o espelhamento de banco de dados antes da operação de renomeação e, em seguida, restabelecer o espelhamento do banco de dados com o novo nome do servidor virtual. Os metadados do espelhamento de banco de dados não serão atualizados automaticamente para refletir o novo nome do servidor virtual.  
  
### <a name="to-rename-a-virtual-server"></a>Para renomear um servidor virtual  
  
1.  Usando o Cluster Administrator, altere o Nome de Rede do SQL para um novo nome.  
  
2.  Coloque o recurso de nome de rede offline. Isso coloca o recurso do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e também outros recursos dependentes offline.  
  
3.  Coloque o recurso do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] online novamente.  
  
## <a name="verify-the-renaming-operation"></a>Verificar a operação de renomeação  
 Depois que um servidor virtual for renomeado, quaisquer conexões que usavam o nome antigo do computador agora deverão ser conectadas usando o novo nome.  
  
 Para verificar se a operação de renomeação foi concluída, selecione informações de `@@servername` ou `sys.servers`. A função `@@servername` retornará o nome do novo servidor virtual, e a tabela `sys.servers` mostrará o nome do novo servidor virtual. Para verificar se o processo de failover está funcionando corretamente com o novo nome, o usuário também deve tentar fazer com o que o recurso do [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] falhe nos outros nós.  
  
 Para as conexões de qualquer nó no cluster, o novo nome poderá ser usado quase imediatamente. No entanto, para as conexões que usam o novo nome de um computador cliente, o novo nome não poderá ser usado para se conectar ao servidor até que o novo nome esteja visível para aquele computador cliente. O tempo necessário para que o novo nome seja propagado por uma rede pode ser de alguns segundos ou de 3 a 5 minutos, dependendo da configuração da rede; poderá ser necessário mais tempo antes de o nome antigo do servidor virtual não estar mais visível na rede.  
  
 Para minimizar o atraso de propagação de rede de um servidor virtual que está renomeando a operação, use as etapas a seguir:  
  
#### <a name="to-minimize-network-propagation-delay"></a>Para minimizar o atraso de propagação de rede  
  
1.  Emita os comandos a seguir a partir de um prompt de comando no nó de servidor:  
  
    ```  
    ipconfig /flushdns  
    ipconfig /registerdns  
    nbtstat -RR  
    ```  
  
## <a name="additional-considerations-after-the-renaming-operation"></a>Considerações adicionais depois da operação de renomeação  
 Depois de renomearmos o nome de rede do cluster de failover, precisamos verificar e executar as instruções a seguir para habilitar todos os cenários no [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent e [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 **[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]:** Depois de alterar o nome de rede de [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] uma instância de cluster de failover usando a ferramenta Administrador de cluster do Windows, a atualização futura ou a operação de desinstalação poderá falhar. Para resolver esse problema, atualize a [entrada do registro](https://go.microsoft.com/fwlink/?LinkId=244002) **ClusterName** seguindo as instruções na seção de resolução destehttps://go.microsoft.com/fwlink/?LinkId=244002)(.  
  
 Serviço do agente: ** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ** Verifique e execute as ações adicionais abaixo para [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] o serviço do Agent:  
  
-   Corrija as configurações do Registro se o SQL Agent estiver configurado para encaminhamento de evento. Para obter mais informações, consulte [Designar um servidor de encaminhamento de eventos &#40;SQL Server Management Studio&#41;](../../../ssms/agent/designate-an-events-forwarding-server-sql-server-management-studio.md).  
  
-   Corrija o servidor mestre (MSX) e os nomes de instância de servidores de destino (TSX) quando os nomes dos computadores e da rede de cluster forem renomeados. Para obter mais informações, consulte estes tópicos:  
  
    -   [Defect Multiple Target Servers from a Master Server](../../../ssms/agent/defect-multiple-target-servers-from-a-master-server.md)  
  
    -   [Criar um ambiente multisservidor](../../../ssms/agent/create-a-multiserver-environment.md)  
  
-   Reconfigure o envio de logs para que o nome de servidor atualizado seja usado para fazer backup e restaurar logs. Para obter mais informações, consulte estes tópicos:  
  
    -   [Configurar o envio de logs &#40;SQL Server&#41;](../../../database-engine/log-shipping/configure-log-shipping-sql-server.md)  
  
    -   [Remover envio de log &#40;SQL Server&#41;](../../../database-engine/log-shipping/remove-log-shipping-sql-server.md)  
  
-   Atualize o Jobsteps que depende do nome do servidor. Para obter mais informações, consulte [Gerenciar etapas de trabalho](../../../ssms/agent/manage-job-steps.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Renomear um computador que hospeda uma instância autônoma do SQL Server](../../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)  
  
  
