---
title: Método SetString (SQLServerCallableStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setString
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f38b97b5-d4f0-4f74-a33d-740241a85842
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ff224739664e55a1e05d45f684f199969903fc04
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67972644"
---
# <a name="setstring-method-sqlservercallablestatement"></a>Método setString (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Define o parâmetro designado como o valor **String** de Java fornecido.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public void setString(java.lang.String sCol,  
                      java.lang.String s)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *sCol*  
  
 Uma **Cadeia de Caracteres** que contém o nome do parâmetro.  
  
 *s*  
  
 Um valor de **String**.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Esse método setString é especificado pelo método setString na interface java.sql.CallableStatement.  
  
 As conversões da cadeia de caracteres em binário só são realizadas quando o [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] sabe que o tipo de destino é binário. Nos casos em que o driver JDBC não souber o tipo subjacente, ele passará o literal **String** e retornará um erro de servidor se o servidor não puder realizar a conversão.  
  
## <a name="see-also"></a>Consulte Também  
 [Membros SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
