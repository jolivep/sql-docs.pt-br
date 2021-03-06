---
title: Método getSendTimeAsDatetime (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 02287122-5dc1-455d-987f-95fd9a69d503
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e1396ac28a7e41dbf530f7e4a251876f6c340871
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67979939"
---
# <a name="getsendtimeasdatetime-method-sqlserverdatasource"></a>Método getSendTimeAsDatetime (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Esse método foi adicionado ao [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0.  
  
 Retorna a configuração da propriedade de conexão **sendTimeAsDatetime** .  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public boolean getSendTimeAsDatetime();  
```  
  
## <a name="return-value"></a>Valor retornado  
 **true** se os valores de Java. Sql. time forem enviados ao servidor como um [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo **DateTime** . **false** se os valores de Java. Sql. time forem enviados ao servidor como um [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo de **hora** .  
  
## <a name="remarks"></a>Remarks  
 Consulte [definindo as propriedades de conexão](../../../connect/jdbc/setting-the-connection-properties.md) para obter mais informações sobre a propriedade de conexão **sendTimeAsDatetime** .  
  
 O [SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md) permite definir programaticamente a propriedade de conexão **sendTimeAsDatetime**.  
  
 Para obter mais informações, consulte Configurando [como os valores de Java. Sql. time são enviados ao servidor](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Membros de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
