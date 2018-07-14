---
title: Configurar FILESTREAM em um cluster de failover | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], setting up on a failover cluster
ms.assetid: 6721f780-20b7-4109-8ddb-ac327310699e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: da6cea56d0fe80797a525c546f80ac9705d360ba
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37412654"
---
# <a name="set-up-filestream-on-a-failover-cluster"></a>Configurar FILESTREAM em um cluster de failover
  Este tópico descreve como habilitar FILESTREAM em um cluster de failover. Antes de tentar este procedimento, você deve entender [clustering de failover](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md) e ter o FILESTREAM habilitado. Para obter informações sobre como habilitar o FILESTREAM, veja [Habilitar e configurar o FILESTREAM](enable-and-configure-filestream.md).  
  
### <a name="to-set-up-filestream-on-a-failover-cluster"></a>Para configurar FILESTREAM em um cluster de failover  
  
1.  Configure o nó primário para o cluster de failover.  
  
     Depois de concluir a configuração, habilite o FILESTREAM no nó primário usando o **SQL Server Configuration Manager**. Isto habilita as configurações que requerem privilégios Admin do Windows. Se acesso remoto for necessário, selecione **Permitir que clientes remotos tenham acesso contínuo aos dados FILESTREAM**. Isso criará um recurso de cluster de compartilhamento de arquivo.  
  
2.  Configure um nó passivo.  
  
     Depois de concluir a configuração, habilite o FILESTREAM no nó passivo usando o **SQL Server Configuration Manager**. O nome especificado para **Nome de Compartilhamento do Windows** deve ser o mesmo em todos os nós no cluster.  
  
3.  Para adicionar mais nós passivos, repita a etapa 2.  
  
4.  Depois que todos os nós forem adicionados, conclua o processo executando o procedimento armazenado sp_configure em cada instância do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
5.  Para adicionar e habilitar nós adicionais ao cluster, em qualquer momento, repita as etapas 2, 3 e 4.  
  
## <a name="see-also"></a>Consulte também  
 [Opções de configuração do servidor &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Criar um novo cluster de failover do SQL Server &#40;Instalação&#41;](../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md)   
 [Remover uma Instância de Cluster de Failover do SQL Server &#40;Instalação&#41;](../../sql-server/failover-clusters/install/remove-a-sql-server-failover-cluster-instance-setup.md)   
 [Adicionar ou remover nós em um cluster de failover do SQL Server &#40;Instalação&#41;](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)  
  
  