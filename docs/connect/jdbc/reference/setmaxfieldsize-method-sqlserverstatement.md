---
title: Método setMaxFieldSize (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.setMaxFieldSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 38f7fc1d-acad-4d10-9fc8-3c0669d93b07
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8958ffe76adbea75959dd15f87db58f28f0893b2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67974000"
---
# <a name="setmaxfieldsize-method-sqlserverstatement"></a>Método setMaxFieldSize (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Define o limite para o número máximo de bytes em uma coluna [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) que armazena caracteres ou valores binários, como o número de bytes fornecido.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public final void setMaxFieldSize(int max)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *max*  
  
 Um **int** que indica o número máximo de bytes.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Esse método setMaxFieldSize é especificado pelo método setMaxFieldSize na interface java. Sql. Statement.  
  
## <a name="see-also"></a>Consulte Também  
 [Membros SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
