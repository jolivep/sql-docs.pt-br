---
title: SQL Server, objeto Dispositivo de Backup | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLServer:Backup Device
- Backup Device object
ms.assetid: 52e7febf-d5e0-4674-945b-aacc40a9ad6e
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 62ba36e83f08cabda85fd71a02d4e22842fb0e8f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36118332"
---
# <a name="sql-server-backup-device-object"></a>SQL Server, objeto Backup Device
  O objeto **Backup Device** oferece contadores para monitorar dispositivos de backup do Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizados para operações de backup e restauração. Monitore os dispositivos de backup quando quiser determinar a taxa de transferência ou o andamento e o desempenho de operações de backup e restauração por dispositivo. Para monitorar a taxa de transferência da operação de backup ou restauração inteira do banco de dados, use o contador **Taxa de Transferência de Backup/Restauração/s** do objeto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Databases** object. Para obter mais informações, consulte [SQL Server, Databases Object](sql-server-databases-object.md).  
  
 Esta tabela descreve o contador do [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Backup Device** .  
  
|Contadores do Dispositivo de Backup do SQL Server|Description|  
|---------------------------------------|-----------------|  
|**Taxa de Transferência do Dispositivo em Bytes/s**|Taxa de transferência de operações de leitura e gravação (em bytes por segundo) de um dispositivo de backup utilizado no backup ou restauração de bancos de dados. Este contador só existe enquanto a operação de backup ou restauração está em execução.|  
  
## <a name="see-also"></a>Consulte também  
 [Dispositivos de backup &#40;SQL Server&#41;](../backup-restore/backup-devices-sql-server.md)   
 [Monitorar o uso de recursos &#40;Monitor do Sistema&#41;](monitor-resource-usage-system-monitor.md)  
  
  