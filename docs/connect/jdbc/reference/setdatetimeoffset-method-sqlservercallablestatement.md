---
title: Método setDateTimeOffset (SQLServerCallableStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9383e14d-c83e-43c5-980c-50a3e0bedc31
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 264de7ac150aca7494a380fbbd4f5b490607c5c6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67974646"
---
# <a name="setdatetimeoffset-method-sqlservercallablestatement"></a>Método setDateTimeOffset (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Esse método foi adicionado ao [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0.  
  
 Define o valor da coluna especificada para o valor da [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public void setDateTimeOffset(String sCol, microsoft.sql.DateTimeOffset t)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *sCol*  
  
 O nome de uma coluna.  
  
 *t*  
  
 O objeto da [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) .  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Você pode recuperar um valor de [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) com [SQLServerCallableStatement. getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md).  
  
 [setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlserverpreparedstatement.md) usa o ordinal da coluna.  
  
## <a name="see-also"></a>Consulte Também  
 [Membros SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
