---
title: Método registerOutParameter para Type e Name | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.registerOutParameter
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f962c912-2475-4e1f-a384-579be2d17f37
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 18c7dad22a4f5314a0bc920c650bcdf0ecd32d52
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67975925"
---
# <a name="registeroutparameter-method-javalangstring-int-javalangstring"></a>Método registerOutParameter (java.lang.String, int, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Registra o parâmetro OUT com o nome especificado para o tipo de JDBC e nome do tipo fornecidos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
public void registerOutParameter(java.lang.String s,  
                                 int n,  
                                 java.lang.String s1)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *s*  
  
 Uma **String** que contém o nome do parâmetro.  
  
 *n*  
  
 Um código do tipo de JDBC, conforme definido em java.sql.Types.  
  
 *s1*  
  
 Uma **String** que contém o nome do tipo SQL totalmente qualificado.  
  
## <a name="exceptions"></a>Exceções  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Esse método registerOutParameter é especificado pelo método registerOutParameter na interface java. Sql. CallableStatement.  
  
## <a name="see-also"></a>Consulte Também  
 [Método registerOutParameter &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)   
 [Membros SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
