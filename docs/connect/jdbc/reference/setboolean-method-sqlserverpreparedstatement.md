---
title: Método SetBoolean (SQLServerPreparedStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setBoolean
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 63397a19-03a2-44bb-b661-7d62c95b6e4e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 62c639c73b629559c36300886781146f3cd14057
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67975027"
---
# <a name="setboolean-method-sqlserverpreparedstatement"></a>Método setBoolean (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Define o parâmetro designado como o valor **boolean** fornecido.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public final void setBoolean(int n,  
                             boolean x)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *n*  
  
 Um **int** que indica o número do parâmetro.  
  
 *x*  
  
 Um **valor** booliano, **true** ou **false**.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Esse método setboolean é especificado pelo método setboolean na interface java.sql.PreparedStatement.  
  
## <a name="see-also"></a>Consulte Também  
 [Membros de SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Classe SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
